

<h1 id="identity_storage_controllers_api_tenants_roles-roles">Roles</h1>

## GetTenantRoles

<a id="opIdRoles_GetTenantRoles"></a>

Get all Roles for a Tenant.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Roles
```

<h3 id="roles_gettenantroles-parameters">Parameters</h3>

`string tenantId`<br/>Id of tenant.</br></br>
`[optional] string query`<br/>Query to execute. Currently not supported.</br></br>`[optional] integer skip`<br/>Number of providers to skip.</br></br>`[optional] integer count`<br/>Max number of providers to return.</br></br>

<h3 id="roles_gettenantroles-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [Role](#schemarole)s|List of Roles found.|
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
    "Description": "string",
    "RoleScope": 1,
    "TenantId": "string",
    "CommunityId": "string",
    "RoleTypeId": "string"
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

## GetTenantRolesHeader

<a id="opIdRoles_GetTenantRolesHeader"></a>

Get header for Roles to get the total number of Roles for a given tenant.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/Roles
```

<h3 id="roles_gettenantrolesheader-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id.</br></br>

<h3 id="roles_gettenantrolesheader-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Headers for Roles found.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Tenant not found.|
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

## PostTenantRole

<a id="opIdRoles_PostTenantRole"></a>

Create a new `Role` for a Tenant.

### Request
```text 
POST /api/v1/Tenants/{tenantId}/Roles
```

### Request Body

Role to create.<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}
```

<h3 id="roles_posttenantrole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant ID.</br></br>

<h3 id="roles_posttenantrole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[Role](#schemarole)|Role created.|
|302|None|A role with the same Id or Name already exists in the Tenant.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant or Role not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|409|[ErrorResponse](#schemaerrorresponse)|A role with some matching values already exists in Tenant.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 201 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

## GetUsersCountForARole

<a id="opIdRoles_GetUsersCountForARole"></a>

Gets the total number of users for a given role.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/Roles/{roleId}/users
```

<h3 id="roles_getuserscountforarole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id for the Role.</br></br>`string roleId`<br/>Role Id.</br></br>

<h3 id="roles_getuserscountforarole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Headers for Roles found.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Tenant or Role not found.|
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

## GetUsersForARole

<a id="opIdRoles_GetUsersForARole"></a>

Get all the Users for a given role.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Roles/{roleId}/users
```

<h3 id="roles_getusersforarole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id.</br></br>`string roleId`<br/>Role Id.</br></br>

<h3 id="roles_getusersforarole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [User](#schemauser)s|Users for a given role.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Tenant or Role not found.|
|500|None|Internal server error.|

### Example response body

> 200 Response

```json
[
  {
    "Id": "string",
    "GivenName": "string",
    "Surname": "string",
    "Name": "string",
    "Email": "string",
    "ContactEmail": "string",
    "ContactGivenName": "string",
    "ContactSurname": "string",
    "ExternalUserId": "string",
    "IdentityProviderId": "string",
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

## GetClientCredentialClientsCountForARole

<a id="opIdRoles_GetClientCredentialClientsCountForARole"></a>

Get the total number of clients for a given role.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/Roles/{roleId}/clientcredentialclients
```

<h3 id="roles_getclientcredentialclientscountforarole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id.</br></br>`string roleId`<br/>Role Id.</br></br>

<h3 id="roles_getclientcredentialclientscountforarole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Headers for the total number of clients for a given role.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Tenant or Role not found.|
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

## GetClientCredentialClientsForARole

<a id="opIdRoles_GetClientCredentialClientsForARole"></a>

Get all the clients for a given role.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Roles/{roleId}/clientcredentialclients
```

<h3 id="roles_getclientcredentialclientsforarole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id.</br></br>`string roleId`<br/>Role Id.</br></br>

<h3 id="roles_getclientcredentialclientsforarole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [ClientCredentialClient](#schemaclientcredentialclient)s|Clients for a given role.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Tenant or Role not found.|
|500|None|Internal server error.|

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

## GetTenantRole

<a id="opIdRoles_GetTenantRole"></a>

Returns the specified Role.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Roles/{roleId}
```

<h3 id="roles_gettenantrole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant Id.</br></br>`string roleId`<br/>Role Id.</br></br>

<h3 id="roles_gettenantrole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Role](#schemarole)|Role specified.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Role or Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}
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

## GetTenantRoleHeader

<a id="opIdRoles_GetTenantRoleHeader"></a>

Get header for a Role on given tenant.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/Roles/{roleId}
```

<h3 id="roles_gettenantroleheader-parameters">Parameters</h3>

`string tenantId`<br/>Id of tenant.</br></br>`string roleId`<br/>Id of provider.</br></br>

<h3 id="roles_gettenantroleheader-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header for Role specified.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|IdentityProvider or Tenant not found.|
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

## PutTenantRole

<a id="opIdRoles_PutTenantRole"></a>

Update a `Role` for a Tenant.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Roles/{roleId}
```

### Request Body

Role to update.<br/>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}
```

<h3 id="roles_puttenantrole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant ID.</br></br>`string roleId`<br/>Role ID.</br></br>

<h3 id="roles_puttenantrole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Role](#schemarole)|Updated Role.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant or Role not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}
```

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Account Administrator</li>
</ul>

## DeleteTenantRole

<a id="opIdRoles_DeleteTenantRole"></a>

Delete a Role from a Tenant.

### Request
```text 
DELETE /api/v1/Tenants/{tenantId}/Roles/{roleId}
```

<h3 id="roles_deletetenantrole-parameters">Parameters</h3>

`string tenantId`<br/>Tenant ID.</br></br>`string roleId`<br/>Role ID.</br></br>

<h3 id="roles_deletetenantrole-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|IdentityProvider or Tenant not found.|
|405|[ErrorResponse](#schemaerrorresponse)|Delete built-in Roles not allowed.|
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

# Schemas

<h2 id="tocS_Role">Role</h2>

<a id="schemarole"></a>
<a id="schema_Role"></a>
<a id="tocSrole"></a>
<a id="tocsrole"></a>

```json
{
  "Id": "string",
  "Name": "string",
  "Description": "string",
  "RoleScope": 1,
  "TenantId": "string",
  "CommunityId": "string",
  "RoleTypeId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Id|string(guid)¦null|false|none|none|
|Name|string¦null|false|none|none|
|Description|string¦null|false|none|none|
|RoleScope|[RoleScope](#schemarolescope)¦null|false|none|none|
|TenantId|string(guid)¦null|false|none|none|
|CommunityId|string(guid)¦null|false|none|none|
|RoleTypeId|string(guid)¦null|false|none|none|

<h2 id="tocS_RoleScope">RoleScope</h2>

<a id="schemarolescope"></a>
<a id="schema_RoleScope"></a>
<a id="tocSrolescope"></a>
<a id="tocsrolescope"></a>

```json
1

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|3|

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

<h2 id="tocS_User">User</h2>

<a id="schemauser"></a>
<a id="schema_User"></a>
<a id="tocSuser"></a>
<a id="tocsuser"></a>

```json
{
  "Id": "string",
  "GivenName": "string",
  "Surname": "string",
  "Name": "string",
  "Email": "string",
  "ContactEmail": "string",
  "ContactGivenName": "string",
  "ContactSurname": "string",
  "ExternalUserId": "string",
  "IdentityProviderId": "string",
  "RoleIds": [
    "string"
  ]
}

```

Object for retrieving a User.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Id|string(guid)|false|none|Gets or sets unique User ID.|
|GivenName|string¦null|false|none|Gets or sets given name of user.|
|Surname|string¦null|false|none|Gets or sets surname of user.|
|Name|string¦null|false|none|Gets or sets name of user.|
|Email|string¦null|false|none|Gets or sets email of user.|
|ContactEmail|string¦null|false|none|Gets or sets contact email for user. User will only be contacted<br />through this email.|
|ContactGivenName|string¦null|false|none|Gets or sets preferred contact name for user.|
|ContactSurname|string¦null|false|none|Gets or sets preferred contact surname for user.|
|ExternalUserId|string¦null|false|none|Gets or sets provider id for user. This is the unique ID we<br />get from the Identity Provider.|
|IdentityProviderId|string(guid)¦null|false|none|Gets or sets Identity Provider Id used to authenticate User.<br />Will be set once the User accepts an invitation.<br />If not specified when sending the invitation to<br />the User, it can be any of the Identity Provider<br />Ids configured for this Tenant.|
|RoleIds|[string]¦null|false|none|Gets or sets list of strings of RoleIds.|

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

