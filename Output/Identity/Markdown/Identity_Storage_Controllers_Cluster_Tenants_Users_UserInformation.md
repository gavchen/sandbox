

<h1 id="identity_storage_controllers_cluster_tenants_users_userinformation-userinformation">UserInformation</h1>

## GetUserInformationForTokenRefresh

<a id="opIdUserInformation_GetUserInformationForTokenRefresh"></a>

Get UserInformation for Access Token Refresh.

### Request
```text 
GET /api/v1/tenants/{tenantId}/users/{userId}/UserInformation
```

<h3 id="userinformation_getuserinformationfortokenrefresh-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string userId`<br/>User Id.</br></br>`string claimTypes`<br/>Claim Types.</br></br>

<h3 id="userinformation_getuserinformationfortokenrefresh-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[UserInformationResponse](#schemauserinformationresponse)|UserInformation or UserInformationMultiStatusResponse.|
|207|[UserInformationMultiStatusResponse](#schemauserinformationmultistatusresponse)|UserInformation or UserInformationMultiStatusResponse.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs, or Client limit exceeded.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|
|503|[ErrorResponse](#schemaerrorresponse)|Dependency service not available.|

### Example response body

> 200 Response

```json
{
  "UserInformation": {
    "property1": [
      "string"
    ],
    "property2": [
      "string"
    ]
  }
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

# Schemas

<h2 id="tocS_UserInformationResponse">UserInformationResponse</h2>

<a id="schemauserinformationresponse"></a>
<a id="schema_UserInformationResponse"></a>
<a id="tocSuserinformationresponse"></a>
<a id="tocsuserinformationresponse"></a>

```json
{
  "UserInformation": {
    "property1": [
      "string"
    ],
    "property2": [
      "string"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|UserInformation|object¦null|false|none|none|
|» **additionalProperties**|[string]|false|none|none|

<h2 id="tocS_UserInformationMultiStatusResponse">UserInformationMultiStatusResponse</h2>

<a id="schemauserinformationmultistatusresponse"></a>
<a id="schema_UserInformationMultiStatusResponse"></a>
<a id="tocSuserinformationmultistatusresponse"></a>
<a id="tocsuserinformationmultistatusresponse"></a>

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "ChildErrors": [
    {
      "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c",
      "Error": "Error message.",
      "Reason": "Reason that caused error.",
      "Resolution": "Possible solution for the error.",
      "StatusCode": 0,
      "ModelId": "string",
      "property1": null,
      "property2": null
    }
  ],
  "Data": {
    "UserInformation": {
      "property1": [
        "string"
      ],
      "property2": [
        "string"
      ]
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|OperationId|string¦null|false|none|none|
|Error|string¦null|false|none|none|
|Reason|string¦null|false|none|none|
|ChildErrors|[[MultiStatusResponseChildError](#schemamultistatusresponsechilderror)]¦null|false|none|none|
|Data|[UserInformationResponse](#schemauserinformationresponse)¦null|false|none|none|

<h2 id="tocS_MultiStatusResponseChildError">MultiStatusResponseChildError</h2>

<a id="schemamultistatusresponsechilderror"></a>
<a id="schema_MultiStatusResponseChildError"></a>
<a id="tocSmultistatusresponsechilderror"></a>
<a id="tocsmultistatusresponsechilderror"></a>

```json
{
  "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c",
  "Error": "Error message.",
  "Reason": "Reason that caused error.",
  "Resolution": "Possible solution for the error.",
  "StatusCode": 0,
  "ModelId": "string",
  "property1": null,
  "property2": null
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[ErrorResponse](#schemaerrorresponse)|false|none|Object returned whenever there is an error.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|ChildError objects returned in a 207 response.|
|» **additionalProperties**|any|false|none|none|
|» StatusCode|integer(int32)|false|none|Gets or sets hTTP status code.|
|» ModelId|string¦null|false|none|Gets or sets model ID.|

<h2 id="tocS_ErrorResponse">ErrorResponse</h2>

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

```json
{
  "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c",
  "Error": "Error message.",
  "Reason": "Reason that caused error.",
  "Resolution": "Possible solution for the error."
}

```

Object returned whenever there is an error.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|**additionalProperties**|any|false|none|none|
|OperationId|string|true|none|Gets or sets operationId of action that caused the Error.|
|Error|string|true|none|Gets or sets error description.|
|Reason|string|true|none|Gets or sets reason for the Error.|
|Resolution|string|true|none|Gets or sets what can be done to resolve the Error.|

