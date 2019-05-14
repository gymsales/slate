# Companies

## The Company Object

>The Company object

```json
{
  "id": 452,
  "external_id": 2895,
  "name": "API Company",
  "email": "apicompany@example.com",
  "phone": "+61447135119",
  "address": "15 Adelaide street",
  "city": "Brisbane",
  "state": "QLD",
  "zip": "4000",
  "country": "AU",
  "time_zone": "Brisbane",
  "work_time_from": "08:00",
  "work_time_into": "20:00",
  "status": "active"
}
```

Name|Type|Description
--------- | ------- | --------
address|string|15 Adelaide street
city|string|Brisbane
country|string|AU
email|string|apicompany@example.com
errors|[errors]()|
external_id|integer|123456
id|integer|438
name|string|API company
phone|string|+61447135119
state|string|QLD
status|string|Company status. Default is `active`. Enumerated Values: `active`, `trial`, `in-active` |`active`
time_zone|string|Brisbane
visitor_app_code|string|Activation code required for visitor app|123456
work_time_from|string|08:00
work_time_into|string|20:00
zip|string|4000


## Create a Company

>`POST /api/v1/companies`

```shell
curl -X POST --user some@ware.com:password \
  "https://login.gymsales.net/api/v1/companies" \
  -d '{"name":"A Company Name", "visitor_app_code":"5893016"}'
```

```http
POST /api/v1/companies HTTP/1.1
Host: login.gymsales.net
Authorization: Basic c29tZUB3YXJlLmNvbTpwYXNzd29yZA==
Content-Type: application/json

{
  "name": "A Company Name",
  "visitor_app_code":"5893016"
}
```

>Response

```json
{
  "id": 452,
  "external_id": 2895,
  "name": "API Company",
  "email": "apicompany@example.com",
  "phone": "+61447135119",
  "address": "15 Adelaide street",
  "city": "Brisbane",
  "state": "QLD",
  "zip": "4000",
  "country": "AU",
  "time_zone": "Brisbane",
  "work_time_from": "08:00",
  "work_time_into": "20:00",
  "status": "active"
}
```

### Arguments

Name|Description|Example
--------- | ------- | ----------- | ------
address|15 Adelaide street
city|Brisbane
country|AU
email|apicompany@example.com
errors|
external_id|123456
id|438
name|API company
phone|+61447135119
state|QLD
status|Company status. Default is `active`. Enumerated Values: `active`, `trial`, `in-active` |`active`
time_zone|Brisbane
visitor_app_code|Activation code required for visitor app|123456
work_time_from|08:00
work_time_into|20:00
zip|4000

### Returns
Returns the company object if succeeded.

## Retrieve a Company

>`GET /api/v1/companies/:company_id`

```shell
curl -X GET --user some@ware.com:password \
  "https://login.gymsales.net/api/v1/companies/452" \
```

```http
GET /api/v1/companies/468 HTTP/1.1
Host: login.gymsales.net
Authorization: Basic c29tZUB3YXJlLmNvbTpwYXNzd29yZA==
```

>Response

```json
{
  "id": 452,
  "external_id": 2895,
  "name": "API Company",
  "email": "apicompany@example.com",
  "phone": "+61447135119",
  "address": "15 Adelaide street",
  "city": "Brisbane",
  "state": "QLD",
  "zip": "4000",
  "country": "AU",
  "time_zone": "Brisbane",
  "work_time_from": "08:00",
  "work_time_into": "20:00",
  "status": "active"
}
```

### Arguments

`company_id` The id of the company to be retrieved

### Returns

Returns the company object

## Update a Company

>`PUT /api/v1/companies/:company_id`

```shell
curl -X PUT --user some@ware.com:password \
  "https://login.gymsales.net/api/v1/companies/452" \
  -d '{"name":"A Company Name", "visitor_app_code":"5893016"}'
```

```http
PUT /api/v1/companies/452 HTTP/1.1
Host: login.gymsales.net
Authorization: Basic c29tZUB3YXJlLmNvbTpwYXNzd29yZA==
Content-Type: application/json

{
  "name": "A Company Name",
  "visitor_app_code":"5893016"
}
```

>Response

```json
{
  "id": 452,
  "external_id": 2895,
  "name": "API Company",
  "email": "apicompany@example.com",
  "phone": "+61447135119",
  "address": "15 Adelaide street",
  "city": "Brisbane",
  "state": "QLD",
  "zip": "4000",
  "country": "AU",
  "time_zone": "Brisbane",
  "work_time_from": "08:00",
  "work_time_into": "20:00",
  "status": "active"
}
```

### Arguments

Name|Description|Example
--------- | ------- | ----------- | ------
address|15 Adelaide street
city|Brisbane
country|AU
email|apicompany@example.com
errors|
external_id|123456
id|438
name|API company
phone|+61447135119
state|QLD
status|Company status. Default is `active`. Enumerated Values: `active`, `trial`, `in-active` |`active`
time_zone|Brisbane
visitor_app_code|Activation code required for visitor app|123456
work_time_from|08:00
work_time_into|20:00
zip|4000

### Returns
Returns the company object if the update succeeded.
