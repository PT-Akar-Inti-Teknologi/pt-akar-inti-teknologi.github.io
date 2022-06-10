---
layout: default
title: API Response
permalink: /standards/backend/api-response
parent: Backend
grand_parent: Standards
nav_order: 2
---

# API Convention

## Response Code

We can use these general response code, depends on monolith or microservice.

### Monolith

> {A}-{B}
>> {A}: Project Code Name
>
>> {B}: HTTP CODE / Sequence Code

Example:
- PTPR-200 (HTTP Code)
- PTPR-00001 (Sequence Code)

### Microservice
> {A}-{B}-{C}
>> {A}: Project Code Name
>
>> {B}: Module Name
>
>> {C}: HTTP CODE / Sequence Code

Example
- PTPR-LOGIN-200 (HTTP Code)
- PTPR-LOGIN-00001 (Sequence Code)

## Response Body
### Success Condition

#### Single Data
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-0000",
		"response_message": "Sukses"
	},
	"response_output": {
		"data_A": "aaaa",
		"data_B": "bbbb"
	}
}
```

#### Collection Data
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-0000",
		"response_message": "Sukses"
	},
	"response_output": {
		"pagination": null,
		"content": [{
				"data_A": "aaaa",
				"data_B": "bbbb"
			},
			{
				"data_A": "aaaa",
				"data_B": "bbbb"
			}
		]
	}
}
```

#### Collection Data with Pagination
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-0000",
		"response_message": "Sukses"
	},
	"response_output": {
		"pagination": {
			"page": 0,
			"total": 100,
			"size": 10
		},
		"content": [{
				"data_A": "aaaa",
				"data_B": "bbbb"
			},
			{
				"data_A": "aaaa",
				"data_B": "bbbb"
			}
		]
	}
}
```

### Error Condition
#### Invalid Parameter
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-00001",
		"response_message": "Parameter tidak valid"
	},
	"response_output": {
		"email": "email format not valid",
		"price": "must numeric"
	}
}
```

#### Server Error
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-500",
		"response_message": "internal server error"
	},
	"response_output": null
}
```

#### Invalid Process
```
{
	"response_schema": {
		"response_code": "PTPR-LOGIN-404",
		"response_message": "User tidak di temukan"
	},
	"response_output": null
}
```