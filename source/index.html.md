---
title: CBS API Specs

<!-- language_tabs: # must be one of https://git.io/vQNgJ -->
  <!-- - json -->

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

<!-- includes: -->
  <!-- - errors -->

search: true
------------

# Approval

## createOrUpdateDraftApplication

```json
{
	"request": {
		"draft_application_details": {
			"usecase": "FIN-GLS-UC001",
			"data": {
				"general_ledger_details": {
					"code": "GL001",
					"name": "General Ledger One",
					"description": "General Ledger Description",
					"external_reference_number": "Ext001",
					"category": "GL_CAT001",
					"currency": "CCY001",
					"balance_type": "CR_BAL",
					"allowed_transaction_type": "CREDIT"
				}
			}
		}
	},

	"headers": {
		"actor_type": "CUSTOMER",
		"operation_mode": "SELF",
		"channel_code": "NOVOPAY",
		"function_sub_code": "CREATE",
		"function_code": "DEFAULT",
		"end_channel_code": "AIG",
		"run_mode": "TRIAL",
		"stan": "1494307057",
		"user_handle_value": "9816923672",
		"client_ip": "127.0.0.1",
		"location": "44.968046,-94.420307",
		"user_handle_type": "MSISDN",
		"tenant_code": "novopay",
		"client_code": "NOVOPAY",
		"transmission_datetime": "1488779072701"
	}
}
```

> The above command returns JSON structured like this:


```json
{
    "draft_application_id": "1",
    "response_status": {
        "code": "100001",
        "message": "Draft created succesfully",
        "status": "SUCCESS"
    }
}
```

This endpoint creates or updates a draft application.

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/createOrUpdateDraftApplication`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | CREATE or UPDATE
fuction_sub_code | DEFAULT

### Request Parameters

Parameter | Description
--------- | -----------
id | The Id of draft application
usecase | Usecase Number
data | Raw JSON Data to be stored as draft

### Response Parameters

Parameter | Description
--------- | -----------
draft_application_id | The Id of draft application
code | Response Code
message | Response Message
status | Response Status



## deleteDraftApplication

```json
{
	"headers": {
		"tenant_code": "novopay",
		"client_code": "NOVOPAY",
		"channel_code": "NOVOPAY",
		"end_channel_code": "CBS",
		"stan": "{{$timestamp}}",
		"client_ip": "127.0.0.1",
		"transmission_datetime": "1488779072701",
		"operation_mode": "SELF",
		"run_mode": "REAL",
		"retry_count": "0",
		"actor_type": "USER",
		"user_handle_type": "MSISDN",
		"user_handle_value": "9816923672",
		"location": "44.968046,-94.420307",
		"function_code": "DEFAULT",
		"function_sub_code": "DEFAULT"
	},
	"request": {
		"draft_application_details": {
			"id": "1"
		}
	}
}
```

> The above command returns JSON structured like this:

```json
{
    "response_status": {
        "code": "100001",
        "message": "Draft deleted succesfully",
        "status": "SUCCESS"
    }
}
```

This endpoint deletes a given draft application.

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/deleteDraftApplication`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | DEFAULT
fuction_sub_code | DEFAULT

### Request Parameters

Parameter | Description
--------- | -----------
id | The Id of the draft application you want to delete

### Response Parameters

Parameter | Description
--------- | -----------
code | Response Code
message | Response Message
status | Response Status

## getApplicationList

```json
 {
 	"request": {
 		"search_criteria": {
 			"user_id": "1",
 			"user_story_code": "GEN-LEDG"
 		},
 		"page_size": "10",
 		"offset": "0",
 		"sort_criteria": {}
 	},
 	"headers": {
 		"actor_type": "CUSTOMER",
 		"operation_mode": "SELF",
 		"channel_code": "NOVOPAY",
 		"function_sub_code": "APPROVAL",
 		"function_code": "APPLICATION",
 		"end_channel_code": "CBS",
 		"run_mode": "TRIAL",
 		"stan": "1494307057",
 		"user_handle_value": "9816923672",
 		"client_ip": "127.0.0.1",
 		"location": "44.968046,-94.420307",
 		"user_handle_type": "MSISDN",
 		"tenant_code": "novopay",
 		"client_code": "NOVOPAY",
 		"transmission_datetime": "1488779072701"
 	}
 }
```

> The above command returns JSON structured like this:

```json
{
	"offset": "0",
	"response_status": {
		"code": "000",
		"message": "Application List fetch Successfully",
		"status": "SUCCESS"
	},
	"application_list": [{
			"usecase": "TAX-COMP-UC001",
			"data": "{\"tax_component_details\":{\"internal_account_defination_id\":\"1\",\"gl_code\":\"tax component 5\",\"code\":\"TAX5\",\"internal_account_defination_name\":\"TAX5\",\"name\":\"tax component 5\",\"currency_value\":\"tax component 5\",\"description\":\"ashdsajh\",\"currency\":\"TAX5\",\"internal_account_defination_code\":\"tax component 5\",\"id\":null,\"gl_name\":\"TAX5\"},\"tax_component_slab_details\":[{\"percentage\":\"4.12345\",\"effective_date\":\"1519842600000\",\"base_amount\":\"10000\"}],\"draft_id\":null,\"application_id\":null}",
			"created_on": "2018-04-02 15:24:27.0",
			"id": "62",
			"status": "PENDING_APPROVAL"
		},
		{
			"usecase": "TAX-COMP-UC001",
			"data": "{\"tax_component_details\":{\"gl_category_value\":\"GNL_CAT_001\",\"code\":\"TAX8\",\"currency_value\":\"INR\",\"description\":\"ashdsajh\",\"internal_account_defination_id\":\"1\",\"gl_code\":\"GL\",\"internal_account_defination_name\":\"IAD1\",\"name\":\"tax component 8\",\"currency\":\"CCY_001\",\"internal_account_defination_code\":\"IAD1\",\"id\":null,\"gl_name\":\"GL1\",\"gl_category\":\"Asset\"},\"tax_component_slab_details\":[{\"end_date\":\"4102425000000\",\"percentage\":\"12.12\",\"base_amount\":\"10000\",\"start_date\":\"1525113000000\"}],\"draft_id\":null,\"application_id\":null}",
			"created_on": "2018-04-05 16:02:33.0",
			"id": "72",
			"status": "PENDING_APPROVAL"
		}
	],
	"number_of_records": "2",
	"page_size": 2
}
```

This endpoint gives list of application(s).

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/getApplicationList`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | APPLICATION or DRAFT
fuction_sub_code | DEFAULT or APPROVAL

### Request Parameters

Parameter | Description
--------- | -----------
user_id | User id of the user.
user_story_code | User Story Code.

### Response Parameters

Parameter | Description
--------- | -----------
code | Response Code
message | Response Message
status | Response Status
offset | Offset
number_of_records | Total number of records found
page_size | Page Size
usecase | Usecase
data | Raw JSON data
status | Application Status
created_on | Date on which data was created
id | Id of the application


## getApplicationCount

```json
 {
 	"request": {
 			"user_id": "1",
 			"user_story_code": "GEN-LEDG"
 	},
 	"headers": {
 		"actor_type": "CUSTOMER",
 		"operation_mode": "SELF",
 		"channel_code": "NOVOPAY",
 		"function_sub_code": "APPROVAL",
 		"function_code": "APPLICATION",
 		"end_channel_code": "CBS",
 		"run_mode": "TRIAL",
 		"stan": "1494307057",
 		"user_handle_value": "9816923672",
 		"client_ip": "127.0.0.1",
 		"location": "44.968046,-94.420307",
 		"user_handle_type": "MSISDN",
 		"tenant_code": "novopay",
 		"client_code": "NOVOPAY",
 		"transmission_datetime": "1488779072701"
 	}
 }
```

> The above command returns JSON structured like this:

```json
{
	"draft_count": "2",
	"pending_action_count": 2
}
```

This endpoint gives count of applications and drafts.

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/getApplicationCount`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | DEFAULT
fuction_sub_code | DEFAULT

### Request Parameters

Parameter | Description
--------- | -----------
user_id | User id of the user.
user_story_code | User Story Code.

### Response Parameters

Parameter | Description
--------- | -----------
code | Response Code.
message | Response Message.
status | Response Status.
draft_count | Total number of drafts.
pending_action_count | Total number of pending application.


## submitApplication

```json
 {
 	"request": {
 		"id": "1",
 		"draft_id": "1",
 		"office_id": "1",
 		"target_api_name": "api_name",
 		"target_api_version": "api_version",
 		"target_api_function_code": "api_function_code",
 		"target_api_function_sub_code": "api_fuction_suv_code",
 		"usecase": "USECASE",
 		"identifier": "IDENTIFIER",
 		"data": "DATA",
 		"attachments": []
 	},
 	"headers": {
 		"actor_type": "CUSTOMER",
 		"operation_mode": "SELF",
 		"channel_code": "NOVOPAY",
 		"function_sub_code": "DEFAULT",
 		"function_code": "SUBMIT",
 		"end_channel_code": "CBS",
 		"run_mode": "TRIAL",
 		"stan": "1494307057",
 		"user_handle_value": "9816923672",
 		"client_ip": "127.0.0.1",
 		"location": "44.968046,-94.420307",
 		"user_handle_type": "MSISDN",
 		"tenant_code": "novopay",
 		"client_code": "NOVOPAY",
 		"transmission_datetime": "1488779072701"
 	}
 }
```

> The above command returns JSON structured like this:

```json
{
	"application_id": "1",
	"response_status": {
		"code": "100001",
		"message": "Application Submitted Successfully",
		"status": "SUCCESS"
	}
}
```

This endpoint submits an application for approval.

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/submitApplication`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | SUBMIT or RESUBMIT
fuction_sub_code | DEFAULT

### Request Parameters

Parameter | Description
--------- | -----------
id | Application Id
draft_id | Draft id
office_id | Office Id
target_api_name | Target API name
target_api_version | Target API version
target_api_function_code | Target API function code
target_api_function_sub_code | Target API function sub code
usecase | Usecase
identifier | Identifier
data | Raw JSON data for usecase
attachments | Attachment Array

### Response Parameters

Parameter | Description
--------- | -----------
code | Response Code.
message | Response Message.
status | Response Status.
application_id | Generated application id.


## approveApplication

```json
 {
 	"request": {
 		"id": "1"
 	},
 	"headers": {
 		"actor_type": "CUSTOMER",
 		"operation_mode": "SELF",
 		"channel_code": "NOVOPAY",
 		"function_sub_code": "DEFAULT",
 		"function_code": "DEFAULT",
 		"end_channel_code": "CBS",
 		"run_mode": "TRIAL",
 		"stan": "1494307057",
 		"user_handle_value": "9816923672",
 		"client_ip": "127.0.0.1",
 		"location": "44.968046,-94.420307",
 		"user_handle_type": "MSISDN",
 		"tenant_code": "novopay",
 		"client_code": "NOVOPAY",
 		"transmission_datetime": "1488779072701"
 	}
 }
```

> The above command returns JSON structured like this:

```json
{
	"response_status": {
		"code": "100001",
		"message": "Application Approved Successfully",
		"status": "SUCCESS"
	}
}
```

This endpoint approved an application for approval.

### HTTP Request

`POST http://localhost:8380/api-gateway/api/v1/approveApplication`

### Header Parameters

Parameter | Description
--------- | -----------
fuction_code | DEFAULT
fuction_sub_code | DEFAULT

### Request Parameters

Parameter | Description
--------- | -----------
id | Id of the application to be approved


### Response Parameters

Parameter | Description
--------- | -----------
code | Response Code.
message | Response Message.
status | Response Status.





