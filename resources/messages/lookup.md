# Messages Lookup

Endpoints:

* [Get a message](#get-channels-id-messages-id)
* [Get messages in a thread](#get-channels-id-messages-id-thread)
* [Get multiple messages](#get-messages)
* [Get messages in a channel](#get-channels-id-messages)
* [Get messages by a user](#get-users-me-messages)


## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span> {#get-channels-id-messages-id .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a message from a channel. The requesting user must have access to the channel or have created the message.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to retrieve a message from.
`message_id`|ID of the message to retrieve.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/5/messages/11" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested message.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Message Object..."}
}
```



## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/thread {#get-channels-id-messages-id-thread .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve messages in the same thread of a channel. All messages will have the same `thread_id` (they are all replies to the same message, or is not a reply to any message). The requesting user must have access to the channel.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from.
`message_id`|ID of the message whose thread to retrieve.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/5/messages/13/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages.

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Message Object..."}
    ]
}
```



## <span class="method method-get">GET</span> /channels/messages {#get-messages .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of specified messages. Will only return the first 200 found.

### Query String Parameters

Name|Description
-|-
`ids`|Comma-separated list of message IDs.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/messages?ids=4,11,12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of the messages found.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...Message Object..."},
        {"...Message Object..."},
        {"...Message Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages {#get-channels-id-messages .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve paginated messages from a channel.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/2/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages from the channel.

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "marker": {
            "name": "channel:0"
        },
        "code": 200
    },
    "data": [
        {"...Message Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/me/messages {#get-users-me-messages .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a paginated list of messages created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Message Object..."}
    ]
}
```