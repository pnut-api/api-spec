# User Lookup

Endpoints:

* [Get a user](#get-users-id)
* [Get multiple users](#get-users)
* [Get app user IDs](#get-apps-me-users-ids)
* [Get app user tokens](#get-apps-me-users-tokens)


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span> {#get-users-id .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a user object.

### URL Parameters

Name|Description
-|-
`user_id`|User ID or username with "@" symbol of the user to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the user object

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "...User Object..."
  }
}
```


## <span class="method method-get">GET</span> /users {#get-users .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of specified user objects. Only retrieves the first 200 found.

### Query String Parameters

Name|Description
-|-
`ids`|Comma-separated list of user IDs or usernames with "@" symbol

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users?ids=4,@ludolphus,1000" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {"...User Object..."},
    {"...User Object..."}
  ]
}
```


## <span class="method method-get">GET</span> /apps/me/users/ids {#get-apps-me-users-ids .endpoint}

Token: <span class="endpoint-meta">app</span>

Retrieve a list of all user IDs that authorize the requesting app. It is not paginated.

Requires an app token.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/apps/me/users/ids" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of user IDs

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    "0",
    "0",
    "0"
  ]
}
```


## <span class="method method-get">GET</span> /apps/me/users/tokens {#get-apps-me-users-tokens .endpoint}

Token: <span class="endpoint-meta">app</span>

Retrieve a list of all user token objects that authorize the requesting app. Not currently paginated.

Requires an app token.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/apps/me/users/tokens" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of user tokens

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {"..User Token..."},
    {"..User Token..."},
    {"..User Token..."}
  ]
}
```