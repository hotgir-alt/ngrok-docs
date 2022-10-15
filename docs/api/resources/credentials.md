import CredentialsCreateRequest from './examples/_credentials_create_request.md';
import CredentialsCreateResponse from './examples/_credentials_create_response.md';
import CredentialsDeleteRequest from './examples/_credentials_delete_request.md';
import CredentialsGetRequest from './examples/_credentials_get_request.md';
import CredentialsGetResponse from './examples/_credentials_get_response.md';
import CredentialsListRequest from './examples/_credentials_list_request.md';
import CredentialsListResponse from './examples/_credentials_list_response.md';
import CredentialsUpdateRequest from './examples/_credentials_update_request.md';
import CredentialsUpdateResponse from './examples/_credentials_update_response.md';

# Tunnel Credentials
------------


## Create Tunnel Credential

Create a new tunnel authtoken credential. This authtoken credential can be used to start a new tunnel session. The response to this API call is the only time the generated token is available. If you need it for future use, you must save it securely yourself.

### Request

POST /credentials

<CredentialsCreateRequest />

#### Parameters

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

### Response

Returns a 201 response  on success

<CredentialsCreateResponse />

#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique tunnel credential resource identifier |
| `uri` | string | URI of the tunnel credential API resource |
| `created_at` | string | timestamp when the tunnel credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `token` | string | the credential's authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## Delete Tunnel Credential

Delete a tunnel authtoken credential by ID

### Request

DELETE /credentials/{id}

<CredentialsDeleteRequest />

### Response

Returns a 204 response with no body on success


## Get Tunnel Credential

Get detailed information about a tunnel authtoken credential

### Request

GET /credentials/{id}

<CredentialsGetRequest />

### Response

Returns a 200 response  on success

<CredentialsGetResponse />

#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique tunnel credential resource identifier |
| `uri` | string | URI of the tunnel credential API resource |
| `created_at` | string | timestamp when the tunnel credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `token` | string | the credential's authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## List Tunnel Credentials

List all tunnel authtoken credentials on this account

### Request

GET /credentials

<CredentialsListRequest />

### Response

Returns a 200 response  on success

<CredentialsListResponse />

#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `credentials` | [Credential](#api-credentials-list-fields-credential) | the list of all tunnel credentials on this account |
| `uri` | string | URI of the tunnel credential list API resource |
| `next_page_uri` | string | URI of the next page, or null if there is no next page |
#### Credential fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique tunnel credential resource identifier |
| `uri` | string | URI of the tunnel credential API resource |
| `created_at` | string | timestamp when the tunnel credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `token` | string | the credential's authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## Update Tunnel Credential

Update attributes of an tunnel authtoken credential by ID

### Request

PATCH /credentials/{id}

<CredentialsUpdateRequest />

#### Parameters

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string |  |
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

### Response

Returns a 200 response  on success

<CredentialsUpdateResponse />

#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique tunnel credential resource identifier |
| `uri` | string | URI of the tunnel credential API resource |
| `created_at` | string | timestamp when the tunnel credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| `token` | string | the credential's authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |