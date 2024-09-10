---
layout: default
title: File Upload
permalink: /standards/backend/file-upload
parent: Backend
grand_parent: Standards
nav_order: 5
---

# File Upload

## Recommendation
- Use multipart/form-data instead of base64
  - base64-encoded data is approximately 33% larger, meaning longer upload times, more bandwidth used
  - API body payloads are larger/too large.
  - Need client's side processor to transform the data from a binary file to a string, and you have to reverse the process on the server side to transform data from a string to a binary file.
- It is recommended to resize the file in server side, to avoid slow loading in the client side.
- It also recommended add validation for mime-type in the server side.
- When file is deleted from table, make sure the file also deleted from storage (S3, local/cloud storage, etc)
  

## Saving File as Multipart/form-data Flow

1. Provide separate table to save file data. For Example "file" table
   
    <table>
      <thead>
        <tr>
          <td>id</td>
        </tr>
        <tr>
          <td>name</td>
        </tr>
        <tr>
          <td>mime_type</td>
        </tr>
        <tr>
          <td>file_path</td>
        </tr>
        <tr>
          <td>is_uploaded</td>
        </tr>
        <tr>
          <td>is_resized (optional)</td>
        </tr>
        <tr>
          <td>resized_size (optional)</td>
        </tr>
        <tr>
          <td>created_at</td>
        </tr>
        <tr>
          <td>modified_at</td>
        </tr>
      </thead>
    </table>

2. Backend need to provide API service, specific to upload the file.
  - May needs to provide destination folder.
   
3. Frontend wil uploads the file to backend, backend will response with file ID.
  - File will be saved in "file" table, and mark the "is_uploaded" with "false"
  - Backend need to check the destination folder, if not exists then need to create it
  - Backend also may need to rename the filename to avoid unexpected overwriting existing file

4. Frontend will use file ID and use it with json payload in the main flow.
  - Backend will save the file ID in the main flow table.
  - After uploaded to backend, backend need to mark the file  data with "is_uploaded" true