

<h1 id="identity_storage_cloudcontrollers_api_communities_users-users">Users</h1>

## AddUserToCommunity

<a id="opIdUsers_AddUserToCommunity"></a>

Add a user to a Community.

### Request
```text 
PUT /api/v1/Tenants/{tenantId}/Communities/{communityId}/Users/{userId}
```

<h3 id="users_addusertocommunity-parameters">Parameters</h3>

`string tenantId`<br/>Id of the Tenant that belongs to this Community</br></br>`string communityId`<br/>Id of Community.</br></br>`string userId`<br/>Id of the User to add to the specified Community.</br></br>

<h3 id="users_addusertocommunity-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|201|[User](#schemauser)|Created.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 201 Response

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

### Authorization

To perform this operation, you must have one of the following roles: </br></br>
<b>Authorized Roles</b> 
<ul>
<li>Community Administrator</li>
<li>Community Moderator</li>
</ul>

## RemoveUserFromCommunity

<a id="opIdUsers_RemoveUserFromCommunity"></a>

Remove a User from a Community.

### Request
```text 
DELETE /api/v1/Tenants/{tenantId}/Communities/{communityId}/Users/{userId}
```

<h3 id="users_removeuserfromcommunity-parameters">Parameters</h3>

`string tenantId`<br/>Id of the Tenant that belongs to this Community.</br></br>`string communityId`<br/>Id of Community.</br></br>`string userId`<br/>Id of the user to remove from the specified Community.</br></br>

<h3 id="users_removeuserfromcommunity-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|Removed.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 400 Response

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
<li>Community Administrator</li>
<li>Community Moderator</li>
</ul>

## GetAllUsers

<a id="opIdUsers_GetAllUsers"></a>

Get a list of all users of the Tenant in this Community.

### Request
```text 
GET /api/v1/Tenants/{tenantId}/Communities/{communityId}/Users
```

<h3 id="users_getallusers-parameters">Parameters</h3>

`string tenantId`<br/>Id of the Tenant that belongs to this Community.</br></br>`string communityId`<br/>Id of Community.</br></br>
`[optional] string query`<br/>Query to execute. Currently not supported.</br></br>`[optional] integer skip`<br/>Number of users to skip.</br></br>`[optional] integer count`<br/>Maximum number of users to return.</br></br>

<h3 id="users_getallusers-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [User](#schemauser)s|Success.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Community roles not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

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
<li>Community Member</li>
</ul>

## GetAllUsersCount

<a id="opIdUsers_GetAllUsersCount"></a>

Get a count of all users of the Tenant in this Community. This endpoint is identical to the
            Get All Users List except it does not return a body.

### Request
```text 
HEAD /api/v1/Tenants/{tenantId}/Communities/{communityId}/Users
```

<h3 id="users_getalluserscount-parameters">Parameters</h3>

`string tenantId`<br/>Id of the calling Tenant that belongs to this Community.</br></br>`string communityId`<br/>Id of Community.</br></br>

<h3 id="users_getalluserscount-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Success.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Community roles not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 400 Response

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
<li>Community Administrator</li>
<li>Community Moderator</li>
<li>Community Member</li>
</ul>

# Schemas

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

