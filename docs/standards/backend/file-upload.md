---
layout: default
title: File Upload
permalink: /standards/backend/file-upload
parent: Backend
grand_parent: Standards
nav_order: 5
---

# File Upload Standard

## Recommendations

- Use `multipart/form-data` instead of base64 encoding.
  - Base64 increases file size by ~33%, leading to higher bandwidth usage and longer upload times.
  - Requires client-side processing to encode and server-side decoding, introducing unnecessary overhead.
- Perform server-side file resizing for image files to reduce payload sent to clients and improve performance.
- Validate MIME type server-side to prevent spoofing and ensure only allowed file types are processed.
- When a file is deleted from the database, ensure the actual file is removed from storage (S3, local disk, etc.).
- Avoid accepting executable files or unknown MIME types.

---

## Recommended File Table Schema

| Column Name      | Type         | Description                              |
|------------------|--------------|------------------------------------------|
| `id`             | UUID         | Primary key                              |
| `original_name`  | text         | Filename as uploaded by the user         |
| `stored_name`    | text         | Renamed filename to prevent conflicts    |
| `mime_type`      | text         | Validated content-type                   |
| `extension`      | varchar      | File extension                           |
| `file_path`      | text         | Path to file location in storage         |
| `storage_type`   | enum         | e.g., `local`, `s3`, `gcs`               |
| `checksum`       | text         | Optional hash for integrity check        |
| `size`           | bigint       | File size in bytes                       |
| `is_uploaded`    | boolean      | True when the upload is complete         |
| `is_resized`     | boolean      | True if the image was resized            |
| `resized_size`   | bigint       | Optional resized file size               |
| `created_at`     | timestamptz  | Record creation timestamp                |
| `updated_at`     | timestamptz  | Last update timestamp                    |

---

## File Upload Flow

### Step 1: Upload File

**Endpoint**: `POST /upload`  
**Payload**: `multipart/form-data`

- Client uploads the file
- Server validates:
  - MIME type and size
  - File extension
- Server actions:
  - Renames file to avoid conflicts
  - Creates folder if needed
  - Saves physical file
  - Inserts record into `files` table
  - Sets `is_uploaded = true`
- Response:
  - `file_id`, `stored_name`, `url`, `size`, etc.

### Step 2: Attach File to Entity

**Endpoint**: `PUT /entity/{id}/file`  
**Payload**: JSON body with `file_id`

- Server checks if:
  - File exists and is uploaded
  - File is allowed for this operation
- File ID is saved as foreign key in the main entity

### Optional: Resize or Post-Process

- Server-side background job resizes or converts file
- Updates `is_resized`, `resized_size`, or adds `cdn_url`

---

## File Deletion Policy

- When a file or related entity is deleted:
  - The file entry in the `files` table should be soft-deleted or removed
  - The physical file should be deleted from storage
  - Consider background jobs or lifecycle policies for large-scale cleanup

---

## Security Best Practices

- Check file MIME type and file extension consistency
- Reject executable or scriptable file types (e.g., `.exe`, `.sh`, `.php`)
- Set upload size limits (e.g., max 5 MB per file)
- Use antivirus scanning for public-facing upload endpoints
- Prefer streamed upload to avoid memory overhead
- Return structured metadata (ID, size, type, download URL)

---

## Download Recommendation

- Protect file download URLs with authentication if needed
- Avoid exposing direct file system paths
