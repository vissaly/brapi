# Configuring Postback URL Address

Breach Report API provides delivery of breach-related notifications to a user-specified URL address (Postback URL Address).

The Postback URL Address must start with `https://` prefix. 

The delivered updates provide information on discovered breaches for the domains and URL addresses that are on the watchlist.

You can manage the Postback URL value using the following operations:

* [Get current Postback URL Address value](#get-postback-url-address)
* [Set or update the Postback URL Address](#set-postback-url-address)
* [Remove the Postback URL Address altogether](#delete-postback-url-address)

<p align="center">
  <br>
  <img width="500" src="./img/chapter-separate.jpg" alt="">
</p>

## Notification Data Example

```json
{
 "emails": [
  {
   "id": "5e4d7b69d537e9321c432612",
   "emailAddress": "test@test.com",
   "breaches": [
    {
     "breachId": 1,
     "url": "http://Example.org",
     "title": "Example.com",
     "compromisedAccounts": 4540,
     "description": "In August 2019, breached files from a news platform Example.org surfaced on the web. The files included email accounts and passwords. The owners of the website have not made an official statement and the service was shut down shortly after hack. ",
     "breachMonth": 8,
     "breachYear": 2019,
     "breachDataTypes": [
      "email",
      "password"
     ]
    }
   ]
  }
 ],
 "domains": [
  {
   "id": "5e4ee6007c5549457f691cad",
   "domainName": "mydomain.com",
   "emails": [
    {
     "id": "5e4ee6267c5549457f691cae",
     "emailAddress": "test@mydomain.com",
     "breaches": [
      {
       "breachId": 3,
       "url": "https://www.mozilla.org/",
       "title": "MaliceSync.Bforce",
       "compromisedAccounts": 1694274,
       "description": "In April 2019, News Services issued an official statement notifying users on discovering a pattern of suspicious login attempts. Apparently attackers gained access to passwords that have been used on breached websites and attempted to login to user accounts.",
       "breachMonth": 3,
       "breachYear": 2019,
       "breachDataTypes": [
        "email",
        "password"
       ]
      }
     ]
    }
   ]
  }
 ]
}
```

<p align="center">
  <br>
  <img width="500" src="./img/chapter-separate.jpg" alt="">
</p>


## Get Postback URL Address

**Request URL**: `{BASE_URL}/api/enterprise/v1/postback`

**Request method:** `GET`

Breach Report APi is designed to send notifications to the customer-specified URL address (postback URL). 

This call returns the current postback URL (if any) the API uses for notifications. 

How to construct the request:

1. Include the API key in the request header.
2. Specify your hashed email in the request body.

### Request Parameters

| Name | Type | Description |
| ------ | ------ | ------ |
| api-key | string | An API key you can generate on the [Portal](https://breachreport.com/portal/user-api). Include this key in the request header. |
| email | string | Email you want to check. |

### Code Examples

```shell
curl --location --request GET '{{BASE_URL}}/api/enterprise/v1/postback' \
--header 'api-key: {{API_KEY}}'
```



```javascript
// Fetch
```

```javascript
// NodeJS
```

```php
// Sample PHP code
``` -->

```python
# Sample Python code - http.client
import http.client
import mimetypes
conn = http.client.HTTPSConnection("{{BASE_URL}}")
payload = ''
headers = {
  'api-key': '{{API_KEY}}'
}
conn.request("GET", "/api/enterprise/v1/postback", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))

# Sample Python code - requests
import requests
url = "{{BASE_URL}}/api/enterprise/v1/postback"
payload = {}
headers = {
  'api-key': '{{API_KEY}}'
}
response = requests.request("GET", url, headers=headers, data = payload)
print(response.text.encode('utf8'))
```

```ruby
require "uri"
require "net/http"

url = URI("{{BASE_URL}}/api/enterprise/v1/postback")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["api-key"] = "{{API_KEY}}"

response = http.request(request)
puts response.read_body
```





> Current Postback URL value

### Response: Current Postback URL value

```json
{
  "status": "success",
  "postbackUrl": "https://example.com:3080/admin/user/test-webhook-url"
}
 
```

| Name | Type | Description |
| ------ | ------ | ------ |
| status | string | Success or error. |
| postbackUrl | string | Postback URL address for notifications. |

> Can't return a Postback URL that's not configured.

### Response: Postback URL not configured

```json
{
  "status": "success",
  "postbackUrl": null
}
```

## Set Postback URL Address

**Request URL**: `{BASE_URL}/api/enterprise/v1/postback`

**Request method:** `POST`

Breach Report APi is designed to send notifications to the customer-specified URL address (postback URL). 

This request accepts a URL address and sets it as a target for customer-focused Breach Report API notifications.  

The Postback URL Address must start with `https://` prefix. 

If a postback URL value was specified before, the call updates it with the new value. 

How to construct the request:

1. Include the API key in the request header.
2. Specify the postback URL in the request body.

### Code Examples

```shell
curl --location --request POST '{{BASE_URL}}/api/enterprise/v1/postback' \
--header 'api-key: {{API_KEY}}' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'url=http://localhost:3080/admin/user/test-webhook-url'
```

```javascript
// Fetch
```

```javascript
// NodeJS
```

```php
// Sample PHP code
```

```python
# Sample Python code - http.client
import http.client
import mimetypes
conn = http.client.HTTPSConnection("{{BASE_URL}}")
payload = 'url=http%3A//localhost%3A3080/admin/user/test-webhook-url'
headers = {
  'api-key': '{{API_KEY}}',
  'Content-Type': 'application/x-www-form-urlencoded'
}
conn.request("POST", "/api/enterprise/v1/postback", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))

# Sample Python code - requests
import requests
url = "{{BASE_URL}}/api/enterprise/v1/postback"

payload = 'url=http%3A//localhost%3A3080/admin/user/test-webhook-url'
headers = {
  'api-key': '{{API_KEY}}',
  'Content-Type': 'application/x-www-form-urlencoded'
}
response = requests.request("POST", url, headers=headers, data = payload)
print(response.text.encode('utf8'))
```

```ruby
require "uri"
require "net/http"
url = URI("{{BASE_URL}}/api/enterprise/v1/postback")
http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["api-key"] = "{{API_KEY}}"
request["Content-Type"] = "application/x-www-form-urlencoded"
request.body = "url=http%3A//localhost%3A3080/admin/user/test-webhook-url"
response = http.request(request)
puts response.read_body 
```

```swift
// Sample Swift Code
```

### Request Parameters

| Name | Type | Description |
| ------ | ------ | ------ |
| api-key | string | An API key you can generate on the [Portal](https://breachreport.com/portal/user-api). Include this key in the request header. |
| url | string | Target postback URL address. |

> Postback URL address has been successfully set.

### Response: Postback URL successfully set

```json
{
  "status": "success",
  "postbackUrl": "https://example.com:3080/admin/user/test-webhook-url"
}
 
```

| Name | Type | Description |
| ------ | ------ | ------ |
| status | string | Success or error. |
| postbackUrl| [string] | The list of credential types that were compromised in the incident. |


> Postback URL Address doesn't start with https.

### Response: Postback URL format not met

```json
{
  "status": "error",
  "message": "Postback URL must started with https and be correct"
}
```

<p align="center">
  <br>
  <img width="500" src="./img/chapter-separate.jpg" alt="">
</p>

## Delete Postback URL Address

**Request URL**: `{BASE_URL}/api/enterprise/v1/postback`

**Request method:** `DEL`

Breach Report APi is designed to send notifications to the customer-specified URL address (postback URL). 

This request deletes the postback URL from the customer's account. As a result of the operation, the API is no longer to send the customers new notifications. 

### Code Examples

```shell
curl --location --request DELETE '{{BASE_URL}}/api/enterprise/v1/postback' \
--header 'api-key: {{API_KEY}}'
```

```c
// Sample C code
```

```csharp
// Sample C# code
```


```go
// Sample Golang comments
```

```http
<!-- Sample HTTP code --> 
```


```java
// Sample Java code
```

```javascript
// Fetch
```

```javascript
// NodeJS
```

```php
// Sample PHP code
```

```python
# Sample Python code - http.client
import http.client
import mimetypes
conn = http.client.HTTPSConnection("{{BASE_URL}}")
payload = ''
headers = {
  'api-key': '{{API_KEY}}'
}
conn.request("DELETE", "/api/enterprise/v1/postback", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))

# Sample Python code - requests
import requests

url = "{{BASE_URL}}/api/enterprise/v1/postback"

payload = {}
headers = {
  'api-key': '{{API_KEY}}'
}

response = requests.request("DELETE", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

```ruby
require "uri"
require "net/http"
url = URI("{{BASE_URL}}/api/enterprise/v1/postback")
http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Delete.new(url)
request["api-key"] = "{{API_KEY}}"
response = http.request(request)
puts response.read_body
```

```swift
// Sample Swift Code
```


### Request Parameters

| Name | Type | Description |
| ------ | ------ | ------ |
| api-key | string | An API key you can generate on the [Portal](https://breachreport.com/portal/user-api). Include this key in the request header. |

> Postback URL configuration has been successfully removed.

### Response: Postback URL removed

```json
{
  "status": "success"
} 
```

> Cannot delete Postback URL value that's not configured.

### Response: Cannot delete Postback URL that's not configured

After attempting to remove a value that hasn't been configured. 

```json
{
  "status": "error",
  "message": "Postback urls does not exist"
}
```