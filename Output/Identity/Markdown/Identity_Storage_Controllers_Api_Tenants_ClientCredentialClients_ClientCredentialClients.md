

<h1 id="identity_storage_controllers_api_tenants_clientcredentialclients_clientcredentialclients-clientcredentialclients">ClientCredentialClients</h1>

## CreateClientCredentialClient

<a id="opIdClientCredentialClients_CreateClientCredentialClient"></a>

Create a Client Credential Client. A Client Id and Client Secret will be generated to perform
            authentication. Make sure to store the Secret somewhere safe as we do not store the
            actual value after the creation step. If you do not have access to the Secret value, we suggest
            deleting the Secret and adding a new one for this Client. Clients have unique Ids in a Tenant.
            Currently there is a limit of 50000 clients (of all types) per Tenant.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/ClientCredentialClients
```

### Request Body

ClientCredentialClientCreate object.<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z"
}
```

<h3 id="clientcredentialclients_createclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>

<h3 id="clientcredentialclients_createclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[ClientCredentialClientCreateResponse](#schemaclientcredentialclientcreateresponse)|Client Credential Client details for Client Credential Client created.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs, or Client limit exceeded.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|409|[ErrorResponse](#schemaerrorresponse)|Client Id already exists.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 201 Response

```json
{
  "Secret": "string",
  "Id": 0,
  "Description": "string",
  "ExpirationDate": "2019-08-24T14:15:22Z",
  "Client": {
    "Id": "string",
    "Name": "string",
    "Enabled": true,
    "AccessTokenLifetime": 0,
    "Tags": [
      "string"
    ],
    "RoleIds": [
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

## GetClientCredentialClients

<a id="opIdClientCredentialClients_GetClientCredentialClients"></a>

Get a list of Client Credential clients from a Tenant.
            Optionally, get a list of requested clients. Total number
            of clients in the Tenant set in the Total-Count header.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/ClientCredentialClients
```

<h3 id="clientcredentialclients_getclientcredentialclients-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>
`[optional] array id`<br/>Unordered list of Client Credential Client Ids. Empty, whitespace or null Ids will be ignored.</br></br>`[optional] array tag`<br/>Only return Clients that have these tags.</br></br>`[optional] string query`<br/>Query to execute. Currently not supported.</br></br>`[optional] integer skip`<br/>Number of clients to skip. Will be ignored if a list of Ids is passed.</br></br>`[optional] integer count`<br/>Maximum number of clients to return. Will be ignored if a list of Ids is passed.</br></br>

<h3 id="clientcredentialclients_getclientcredentialclients-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [ClientCredentialClient](#schemaclientcredentialclient)s|Client Credential Clients found.|
|207|[ClientCredentialClientMultiStatusResponse](#schemaclientcredentialclientmultistatusresponse)|Client Credential Clients found.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
[
  {
    "Id": "string",
    "Name": "string",
    "Enabled": true,
    "AccessTokenLifetime": 0,
    "Tags": [
      "string"
    ],
    "RoleIds": [
      "string"
    ]
  }
]
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
</ul>

<b>Strict Roles</b>
<ul>
<li>Account Administrator</li>
</ul>

## GetClientCredentialClientsHeader

<a id="opIdClientCredentialClients_GetClientCredentialClientsHeader"></a>

Return total number of Client Credential clients in a Tenant.
            Optionally, check based on a list of requested clients. The
            value will be set in the Total-Count header. This endpoint
            is identical to the GET one but it does not return any objects
            in the body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/ClientCredentialClients
```

<h3 id="clientcredentialclients_getclientcredentialclientsheader-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>
`[optional] array id`<br/>Unordered list of Client Credential Client Ids. Empty, whitespace or null Ids will be ignored.</br></br>`[optional] array tag`<br/>Only count Clients that have these tags.</br></br>

<h3 id="clientcredentialclients_getclientcredentialclientsheader-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Client Credential Client Headers found.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Client or Tenant not found.|
|500|None|Internal server error.|

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
</ul>

<b>Strict Roles</b>
<ul>
<li>Account Administrator</li>
</ul>

## UpdateClientCredentialClient

<a id="opIdClientCredentialClients_UpdateClientCredentialClient"></a>

Update a Client Credential Client. It can take up to one hour
            for these values to manifest in the authentication process.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

### Request Body

ClientCredentialClient object. Properties that are not set or are null will not be changed.<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

<h3 id="clientcredentialclients_updateclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of Client.</br></br>

<h3 id="clientcredentialclients_updateclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ClientCredentialClient](#schemaclientcredentialclient)|Client Credential Client updated.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or Tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

## GetClientCredentialClient

<a id="opIdClientCredentialClients_GetClientCredentialClient"></a>

Get a Client Credential Client.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

<h3 id="clientcredentialclients_getclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of Client.</br></br>

<h3 id="clientcredentialclients_getclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ClientCredentialClient](#schemaclientcredentialclient)|Client Credential Client specified.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
<li>Self</li>
</ul>

<b>Strict Roles</b>
<ul>
<li>Account Administrator</li>
</ul>

## DeleteClientCredentialClient

<a id="opIdClientCredentialClients_DeleteClientCredentialClient"></a>

Delete a Client Credential Client. It can take up to one hour
            for deletion to manifest in the authentication process. Access
            tokens issued to this Client will be valid until their expiration.

### Request
```text 
DELETE /api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

<h3 id="clientcredentialclients_deleteclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of Client.</br></br>

<h3 id="clientcredentialclients_deleteclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or Tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 401 Response

```json
{
  "OperationId": "1b2af18e-8b27-4f86-93e0-6caa3e59b90c",
  "Error": "Error message.",
  "Reason": "Reason that caused error.",
  "Resolution": "Possible solution for the error."
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

## GetClientCredentialClientHeader

<a id="opIdClientCredentialClients_GetClientCredentialClientHeader"></a>

Validate that a Client Credential Client exists.
            This endpoint is identical to the GET one but
            it does not return any objects in the body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

<h3 id="clientcredentialclients_getclientcredentialclientheader-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of Client.</br></br>

<h3 id="clientcredentialclients_getclientcredentialclientheader-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header for specified Client Credential Client.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Client or Tenant not found.|
|500|None|Internal server error.|

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
<li>Self</li>
</ul>

<b>Strict Roles</b>
<ul>
<li>Account Administrator</li>
</ul>

## GetV1PreviewClientCredentialClients

<a id="opIdClientCredentialClients_GetV1PreviewClientCredentialClients"></a>

Get all Client Credential Clients.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/ClientCredentialClients
```

<h3 id="clientcredentialclients_getv1previewclientcredentialclients-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>
`[optional] array tag`<br/>Only return Clients that have these tags.</br></br>`[optional] string query`<br/>Query to execute. Currently not supported.</br></br>`[optional] integer skip`<br/>Number of clients to skip. From query.</br></br>`[optional] integer count`<br/>Maximum number of clients to return.</br></br>

<h3 id="clientcredentialclients_getv1previewclientcredentialclients-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [ClientCredentialClient2](#schemaclientcredentialclient2)s|List of ClientCredentialClients found.|
|207|[ClientCredentialClientMultiStatusResponse2](#schemaclientcredentialclientmultistatusresponse2)|List of ClientCredentialClients found.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
[
  {
    "ClientId": "string",
    "Id": "string",
    "Name": "string",
    "Enabled": true,
    "Tags": [
      "string"
    ],
    "RoleIds": [
      "string"
    ]
  }
]
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
</ul>

## CreateV1PreviewClientCredentialClient

<a id="opIdClientCredentialClients_CreateV1PreviewClientCredentialClient"></a>

Create a Client Credential flow Client.

### Request
```text 
POST /api/v1-preview/Tenants/{tenantId}/ClientCredentialClients
```

### Request Body

New ClientCredentialClientCreate object.<br/>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z"
}
```

<h3 id="clientcredentialclients_createv1previewclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>

<h3 id="clientcredentialclients_createv1previewclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[ClientCredentialClientResponse](#schemaclientcredentialclientresponse)|Hybrid Client created.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs, or Client limit exceeded.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|409|[ErrorResponse](#schemaerrorresponse)|Client Id already exists.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 201 Response

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z",
  "ClientSecret": "string",
  "SecretId": "string"
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

## GetV1PreviewClientCredentialClient

<a id="opIdClientCredentialClients_GetV1PreviewClientCredentialClient"></a>

Get a Client Credential Client.

### Request
```text 
GET /api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

<h3 id="clientcredentialclients_getv1previewclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of client.</br></br>

<h3 id="clientcredentialclients_getv1previewclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ClientCredentialClient2](#schemaclientcredentialclient2)|ClientCredentialClient specified.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Member</li>
</ul>

## UpdateV1PreviewClientCredentialClient

<a id="opIdClientCredentialClients_UpdateV1PreviewClientCredentialClient"></a>

Update a Client Credential Client.

### Request
```text 
PUT /api/v1-preview/Tenants/{tenantId}/ClientCredentialClients/{clientId}
```

### Request Body

Updated Client Credential Client values.<br/>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

<h3 id="clientcredentialclients_updatev1previewclientcredentialclient-parameters">Parameters</h3>

`string tenantId`<br/>Id of Tenant.</br></br>`string clientId`<br/>Id of client.</br></br>

<h3 id="clientcredentialclients_updatev1previewclientcredentialclient-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[ClientCredentialClient2](#schemaclientcredentialclient2)|Updated ClientCredentialClient.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Client or Tenant not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

# Schemas

<h2 id="tocS_ClientCredentialClientCreateResponse">ClientCredentialClientCreateResponse</h2>

<a id="schemaclientcredentialclientcreateresponse"></a>
<a id="schema_ClientCredentialClientCreateResponse"></a>
<a id="tocSclientcredentialclientcreateresponse"></a>
<a id="tocsclientcredentialclientcreateresponse"></a>

```json
{
  "Secret": "string",
  "Id": 0,
  "Description": "string",
  "ExpirationDate": "2019-08-24T14:15:22Z",
  "Client": {
    "Id": "string",
    "Name": "string",
    "Enabled": true,
    "AccessTokenLifetime": 0,
    "Tags": [
      "string"
    ],
    "RoleIds": [
      "string"
    ]
  }
}

```

Secret information returned after a Client Credential Client is created.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Secret|string¦null|false|none|Gets or sets client secret.|
|Id|integer(int32)|false|none|Gets or sets secret Id.|
|Description|string¦null|false|none|Gets or sets description for the initial secret for the client.|
|ExpirationDate|string(date-time)¦null|false|none|Gets or sets expiration date for the initial secret for the client.|
|Client|[ClientCredentialClient](#schemaclientcredentialclient)¦null|false|none|Gets or sets client Client Credential Client created.|

<h2 id="tocS_ClientCredentialClient">ClientCredentialClient</h2>

<a id="schemaclientcredentialclient"></a>
<a id="schema_ClientCredentialClient"></a>
<a id="tocSclientcredentialclient"></a>
<a id="tocsclientcredentialclient"></a>

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Client](#schemaclient)|false|none|Base object used during Client creation.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|Object to get or update a Client Credential Client.|
|» RoleIds|[string]¦null|false|none|Gets or sets list of Roles to be assigned to this client. Member role is always required.<br />For security reasons we advise against assigning Admin roles to a client.|

<h2 id="tocS_Client">Client</h2>

<a id="schemaclient"></a>
<a id="schema_Client"></a>
<a id="tocSclient"></a>
<a id="tocsclient"></a>

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ]
}

```

Base object used during Client creation.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Id|string¦null|false|none|Gets or sets client ID for this client. This ID should be a GUID.|
|Name|string¦null|false|none|Gets or sets name of Client.|
|Enabled|boolean¦null|false|none|Gets or sets whether client is enabled. Client can be used for authentication<br />if set to true. Client cannot be used for authentication if set to false.|
|AccessTokenLifetime|integer(int32)¦null|false|none|Gets or sets lifetime of access token issued for this client after authentication.<br />Minimum 60 seconds. Maximum 3600 seconds. Defaults to 3600 seconds.|
|Tags|[string]¦null|false|none|Gets or sets for OSIsoft internal use only.|

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

<h2 id="tocS_ClientCredentialClientCreate">ClientCredentialClientCreate</h2>

<a id="schemaclientcredentialclientcreate"></a>
<a id="schema_ClientCredentialClientCreate"></a>
<a id="tocSclientcredentialclientcreate"></a>
<a id="tocsclientcredentialclientcreate"></a>

```json
{
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "AccessTokenLifetime": 0,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[ClientCredentialClient](#schemaclientcredentialclient)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|Object used during Client creation.|
|» SecretDescription|string¦null|false|none|Gets or sets description for the initial secret for the client. Ensure that this is descriptive enough,<br />as it will be the only way to distinguish between multiple secrets and their usage for a<br />client.|
|» SecretExpirationDate|string(date-time)¦null|false|none|Gets or sets expiration date for the initial secret for the client. If set to null the secret will<br />never expire. We advise against such practice.|

<h2 id="tocS_ClientCredentialClientMultiStatusResponse">ClientCredentialClientMultiStatusResponse</h2>

<a id="schemaclientcredentialclientmultistatusresponse"></a>
<a id="schema_ClientCredentialClientMultiStatusResponse"></a>
<a id="tocSclientcredentialclientmultistatusresponse"></a>
<a id="tocsclientcredentialclientmultistatusresponse"></a>

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
  "Data": [
    {
      "Id": "string",
      "Name": "string",
      "Enabled": true,
      "AccessTokenLifetime": 0,
      "Tags": [
        "string"
      ],
      "RoleIds": [
        "string"
      ]
    }
  ]
}

```

MultiStatusResponse objects returned in a 207 response.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|OperationId|string¦null|false|none|Gets or sets operationId that resulted in this error.|
|Error|string¦null|false|none|Gets or sets string message describing the error.|
|Reason|string¦null|false|none|Gets or sets reason that caused the error.|
|ChildErrors|[[MultiStatusResponseChildError](#schemamultistatusresponsechilderror)]¦null|false|none|Gets or sets list of ChildErrors.|
|Data|[[ClientCredentialClient](#schemaclientcredentialclient)]¦null|false|none|Gets or sets data.|

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

<h2 id="tocS_ClientCredentialClient2">ClientCredentialClient2</h2>

<a id="schemaclientcredentialclient2"></a>
<a id="schema_ClientCredentialClient2"></a>
<a id="tocSclientcredentialclient2"></a>
<a id="tocsclientcredentialclient2"></a>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ]
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Client2](#schemaclient2)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» RoleIds|[string]¦null|false|none|none|

<h2 id="tocS_Client2">Client2</h2>

<a id="schemaclient2"></a>
<a id="schema_Client2"></a>
<a id="tocSclient2"></a>
<a id="tocsclient2"></a>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ClientId|string¦null|false|none|none|
|Id|string¦null|false|none|none|
|Name|string¦null|false|none|none|
|Enabled|boolean¦null|false|none|none|
|Tags|[string]¦null|false|none|none|

<h2 id="tocS_ClientCredentialClientMultiStatusResponse2">ClientCredentialClientMultiStatusResponse2</h2>

<a id="schemaclientcredentialclientmultistatusresponse2"></a>
<a id="schema_ClientCredentialClientMultiStatusResponse2"></a>
<a id="tocSclientcredentialclientmultistatusresponse2"></a>
<a id="tocsclientcredentialclientmultistatusresponse2"></a>

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
  "Data": [
    {
      "ClientId": "string",
      "Id": "string",
      "Name": "string",
      "Enabled": true,
      "Tags": [
        "string"
      ],
      "RoleIds": [
        "string"
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|OperationId|string¦null|false|none|none|
|Error|string¦null|false|none|none|
|Reason|string¦null|false|none|none|
|ChildErrors|[[MultiStatusResponseChildError](#schemamultistatusresponsechilderror)]¦null|false|none|none|
|Data|[[ClientCredentialClient2](#schemaclientcredentialclient2)]¦null|false|none|none|

<h2 id="tocS_ClientCredentialClientResponse">ClientCredentialClientResponse</h2>

<a id="schemaclientcredentialclientresponse"></a>
<a id="schema_ClientCredentialClientResponse"></a>
<a id="tocSclientcredentialclientresponse"></a>
<a id="tocsclientcredentialclientresponse"></a>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z",
  "ClientSecret": "string",
  "SecretId": "string"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[ClientCredentialClientCreate2](#schemaclientcredentialclientcreate2)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» ClientSecret|string¦null|false|none|none|
|» SecretId|string¦null|false|none|none|

<h2 id="tocS_ClientCredentialClientCreate2">ClientCredentialClientCreate2</h2>

<a id="schemaclientcredentialclientcreate2"></a>
<a id="schema_ClientCredentialClientCreate2"></a>
<a id="tocSclientcredentialclientcreate2"></a>
<a id="tocsclientcredentialclientcreate2"></a>

```json
{
  "ClientId": "string",
  "Id": "string",
  "Name": "string",
  "Enabled": true,
  "Tags": [
    "string"
  ],
  "RoleIds": [
    "string"
  ],
  "SecretDescription": "string",
  "SecretExpirationDate": "2019-08-24T14:15:22Z"
}

```

### Properties

allOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[ClientCredentialClient2](#schemaclientcredentialclient2)|false|none|none|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» SecretDescription|string¦null|false|none|none|
|» SecretExpirationDate|string(date-time)¦null|false|none|none|

