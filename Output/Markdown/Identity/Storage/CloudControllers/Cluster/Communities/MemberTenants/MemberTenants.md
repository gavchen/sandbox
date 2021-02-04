

<h1 id="identity-storage-cloudcontrollers-cluster-communities-membertenants-membertenants-membertenants">MemberTenants</h1>

## GetAllMemberTenantsInfo

<a id="opIdMemberTenants_GetAllMemberTenantsInfo"></a>

Gets the list of all Tenants and its count of Users in a Community.

### Request
```text 
GET /cluster/Communities/{communityId}/MemberTenants
```

<h3 id="membertenants_getallmembertenantsinfo-parameters">Parameters</h3>

`string communityId`<br/>Id of the Community.<br/><br/>

<h3 id="membertenants_getallmembertenantsinfo-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|List of [MemberTenant](#schemamembertenant)s|A `IEnumerable`1` representing info for each Tenant of a Community.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Community Not Found.|
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

## GetAllMemberTenantsInfoHeader

<a id="opIdMemberTenants_GetAllMemberTenantsInfoHeader"></a>

Gets the number of Member Tenants in a Community.

### Request
```text 
HEAD /cluster/Communities/{communityId}/MemberTenants
```

<h3 id="membertenants_getallmembertenantsinfoheader-parameters">Parameters</h3>

`string communityId`<br/>Id of the Community.<br/><br/>

<h3 id="membertenants_getallmembertenantsinfoheader-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|None|A count of total Community Tenants in a Community.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Community Not Found.|
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

## GetMemberTenantInfo

<a id="opIdMemberTenants_GetMemberTenantInfo"></a>

Gets the Member Tenant info for a Member Tenant in a Community.

### Request
```text 
GET /cluster/Communities/{communityId}/MemberTenants/{memberTenantId}
```

<h3 id="membertenants_getmembertenantinfo-parameters">Parameters</h3>

`string communityId`<br/>Id of the Community.<br/><br/>`string memberTenantId`<br/>Id of the specified community Member Tenant.<br/><br/>

<h3 id="membertenants_getmembertenantinfo-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[MemberTenant](#schemamembertenant)|A `MemberTenant` representing info for a single Tenant of a Community.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant or Community Not Found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

### Example response body

> 200 Response

```json
{
  "Id": "string",
  "TenantName": "string",
  "UserCount": 0,
  "ClientCount": 0
}
```

## AddMemberTenantToCommunity

<a id="opIdMemberTenants_AddMemberTenantToCommunity"></a>

Adds a Member Tenant to a Community.

### Request
```text 
POST /cluster/Communities/{communityId}/MemberTenants/{memberTenantId}
```

### Request Body

Member Tenant to be added.<br/>

```json
{
  "Id": "string",
  "AcceptingUserId": "string"
}
```

<h3 id="membertenants_addmembertenanttocommunity-parameters">Parameters</h3>

`string communityId`<br/>Id of Community.<br/><br/>`string memberTenantId`<br/>Id of Member Tenant.<br/><br/>

<h3 id="membertenants_addmembertenanttocommunity-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|200|[Role](#schemarole)|Success.|
|400|[ErrorResponse](#schemaerrorresponse)|BadRequest.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Community, Tenant, or User not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Operation timed out.|
|409|[ErrorResponse](#schemaerrorresponse)|Tenant already exists in Community.|
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

## RemoveMemberTenantFromCommunity

<a id="opIdMemberTenants_RemoveMemberTenantFromCommunity"></a>

Removes a Member Tenant from a Community.

### Request
```text 
DELETE /cluster/Communities/{communityId}/MemberTenants/{memberTenantId}
```

<h3 id="membertenants_removemembertenantfromcommunity-parameters">Parameters</h3>

`string communityId`<br/>Id of Community.<br/><br/>`string memberTenantId`<br/>Id of Member Tenant.<br/><br/>

<h3 id="membertenants_removemembertenantfromcommunity-responses">Responses</h3>

|Status Code|Body Type|Description|
|---|---|---|
|204|None|No content.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Member Tenant not found.|
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

# Schemas

<h2 id="tocS_MemberTenant">MemberTenant</h2>

<a id="schemamembertenant"></a>
<a id="schema_MemberTenant"></a>
<a id="tocSmembertenant"></a>
<a id="tocsmembertenant"></a>

```json
{
  "Id": "string",
  "TenantName": "string",
  "UserCount": 0,
  "ClientCount": 0
}

```

Object representing a Member Tenant within a Community.

### Properties

|Name|Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Gets or sets id for this Community Member Tenant.|
|TenantName|string|false|false|Gets or sets short identifier for Tenant.|
|UserCount|int32|false|false|Gets or sets the Community users count for this Member Tenant.|
|ClientCount|int32|false|false|Gets or sets the Community client count for this Member Tenant. Placeholder for PBI: 164204 and 158844|

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

|Name|Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Gets or sets operationId of action that caused the Error.|
|Error|string|true|false|Gets or sets error description.|
|Reason|string|true|false|Gets or sets reason for the Error.|
|Resolution|string|true|false|Gets or sets what can be done to resolve the Error.|

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

|Name|Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|true|None|
|Name|string|false|true|None|
|Description|string|false|true|None|
|RoleScope|[RoleScope](#schemarolescope)|false|true|None|
|TenantId|guid|false|true|None|
|CommunityId|guid|false|true|None|
|RoleTypeId|guid|false|true|None|

<h2 id="tocS_RoleScope">RoleScope</h2>

<a id="schemarolescope"></a>
<a id="schema_RoleScope"></a>
<a id="tocSrolescope"></a>
<a id="tocsrolescope"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|Account|1|
|Community|2|
|Cluster|3|

<h2 id="tocS_MemberTenantAdd">MemberTenantAdd</h2>

<a id="schemamembertenantadd"></a>
<a id="schema_MemberTenantAdd"></a>
<a id="tocSmembertenantadd"></a>
<a id="tocsmembertenantadd"></a>

```json
{
  "Id": "string",
  "AcceptingUserId": "string"
}

```

Object used to add a Member Tenant to a Community.

### Properties

|Name|Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Gets or sets Id of Tenant being invited.|
|AcceptingUserId|guid|false|false|Gets or sets Id of User accepting invitation on behalf of Tenant.|

