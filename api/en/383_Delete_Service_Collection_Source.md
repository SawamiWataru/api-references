# Service Collection Source Delete

## Overview

Delete service source information

### Required Privileges

write


## Request

### Request URL

```
/{UnitFQDN}/{CellName}/{BoxName}/{CollectionName}/__src/{ResourceName}
```

|Path|Overview|Notes|
|:--|:--|:--|
|{CellName}|Cell Name||
|{BoxName}|Box Name||
|{CollectionName}|Service Collection Name|Valid values <br>Number of digits:1-128<br>Usable character types<br>alphanumeric character, period(.), under score(_), hyphen(-)|
|{ResourceName}|Resource name|Valid values(limit) <br>Number of digits:1-128<br>Usable character types<br>alphanumeric character, period(.), under score(_), hyphen(-)|

### Request Method

DELETE

### Request Query

#### Common Request Query

|Query Name|Overview|Effective Value|Required|Notes|
|:--|:--|:--|:--|:--|
|p_cookie_peer|Cookie Authentication Value|The cookie authentication value returned from the server during authentication|No|Valid only if no Authorization header specified<br>Specify this when cookie authentication information is to be used|

### Request Header

#### Common Request Header

|Header Name|Overview|Effective Value|Required|Notes|
|:--|:--|:--|:--|:--|
|X-HTTP-Method-Override|Method override function|User-defined|No|If you specify this value when requesting with the POST method, the specified value will be used as a method.|
|X-Override|Header override function|${OverwrittenHeaderName}:${Value}|No|Overwrite normal HTTP header value. To overwrite multiple headers, specify multiple X-Override headers.|
|X-Personium-RequestKey|RequestKey field value output in the event log|Single-byte alphanumeric characters, hyphens ("-"), and underscores ("_")<br>Maximum of 128 characters|No||

### Request Header

|Header Name|Overview|Effective Value|Required|Notes|
|:--|:--|:--|:--|:--|
|Authorization|Specifies authentication information in the OAuth 2.0 format|Bearer {AccessToken}|No|* Authentication tokens are the tokens acquired using the Authentication Token Acquisition API|

#### Service source delete request header

|Header Name|Overview|Effective Value|Required|Notes|
|:--|:--|:--|:--|:--|
|If-Match|Specify resource version information|String|Yes|If you do not specify a version*(asterisk)|

### Request Body

None


## Response

### Response Code

|Code|Message|Overview|
|:--|:--|:--|
|204|No Content|When update is successful|

### Response Header

None

### Response Body

None

### Error Messages

Refer to [Error Message List](004_Error_Messages.md)


## cURL Command

```sh
curl "https://{UnitFQDN}/{CellName}/{BoxName}/{CollectionName}/__src/{ResourceName}" -X \
DELETE -i -H 'Authorization: Bearer {AccessToken}' -H 'Accept: application/json'
```


