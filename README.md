<p align="center">
  <br>
  <img width="200" src="./img/logo.png" alt="">
  <br>
  <br>
</p>

<link rel="stylesheet" type="text/css" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=A%20good,%20solid%20app%20to%20keep%20your%20keys%20safe.&url=https://keychain.array.io/&via=ProjectArray&hashtags=cybersecurity,private,cryptography,blockchain,app) [![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)](https://github.com/arrayio/array-io-keychain#contributing-to-the-project)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/arrayio/array-io-keychain/blob/master/LICENSE.md) [![npm version](https://badge.fury.io/js/keychain.js.svg)](https://badge.fury.io/js/keychain.js) ]

# Overview

The SuperAPI team monitors the internet for information about data breaches. Currently, our database contains information about over 12B compromised user accounts. Your applications can access this information via SuperAPI.

<p align="center">
  <br>
  <img width="500" src="./img/superapi.png" alt="">
  <br>
</p>


## Getting started

Before using SuperAPI, make sure you've registered at [SuperAPI portal](https://superapi.com) so you can use [the unique API key](https://github.com/vissaly/brapi/blob/master/docs/get-api-key.md). 

When you use SuperAPI, include the API key to each request header. 

## Testing SuperAPI

SuperAPI can be tested using various automation tools.

SuperAPI request schema for Postman is available at the link below.

https://www.getpostman.com/collections/123456

The following parameters can be specified via the test environment.

| PARAMETER | VALUE | COMMENTS |
| ------ | ------ | ------ |
| BASE_URL | `https://superapi.com` |  |
| API_KEY | `your-secret-key` | See [Generating the API key](https://github.com/vissaly/brapi/blob/master/docs/get-api-key.md) for details. |

## How to Use SuperAPI

* [Check Email Addresses and Domains]()
* [Register Email Addresses and Domains]()
* [Monitor Email Addresses and Domains]()
* [Configure the Postback URL and Be Updated]()


## Contact 

If you need help integrating with Breach Report API or need additional information, don't hesitate to contact us on:

* Telegram
* Stackoverflow
* Twitter

Or email us at info@breachreport.com.
If you want to report a security issue, include the word "security" in the subject field.

We take security issues very seriously and we'll be looking forward to hearing from you. Still, we hope you enjoy using KeyChain and the integration goes smooth!

## License 




<p align="center">
  <br>
  <img width="500" src="./img/chapter-separate.jpg" alt="">
</p>

## Response Codes

| Code | Name | Description |
| ------ | ------ | ------ |
| 200 | OK | Request successfully passed. |
| 400 | Bad Request | Invalid domain URL. Please check the Base URL value. |
| 401 | Unauthorized | The `API-Key` value is invalid or is missing from the header. Make sure that you have generated one at [Portal](https://breachreport.com/portal/user-api) section. |
| 402 | Payment required | You may need to upgrade your subscription. For further information, visit the [Subscription](https://breachreport.com/portal/subscriptions) page. |
| 409 | Conflict | The domain name or the email address was registered before. Check your account for existing domains / emails. |
| 500 | Internal server error | Internal server error occured. If this issue persists, contact our Support Service. |