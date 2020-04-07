# /api/graphql

{% api-method method="post" host="https://www.tezoslive.io" path="/api/graphql" %}
{% api-method-summary %}
GraphQL
{% endapi-method-summary %}

{% api-method-description %}
In order to query  the `/graphql` endpoint you need to provide   
`x-taas-key` in the request. You also need to provide your GraphQL query in the request body.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-taas-key" type="string" required=true %}
Your TaaS GraphQL API endpoint key
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=true %}
`GraphQL query object`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
GraphQL JSON response based on your query
{% endapi-method-response-example-description %}

```
{
  "data": {
    "block": {
      "protocol": "PsCARTHAGazKbHtnKfLzQg3kms52kSRpgnDY982a9oYsSXRLQEb",
      "chain_id": "NetXdQprcVkpaWU",
      "hash": "BM7MCim4kxofsoP8Zaw7k8MRBqNWP9tAPnWQDLoz8i9mMjk7ssh",
      "header": {
        "level": 884753,
        "timestamp": "2020-03-28T12:43:07Z"
      }
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
The API key provided in the `X-TaaS-Key` header is not valid, or the header is not provided.
{% endapi-method-response-example-description %}

```
Unauthorized
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=429 %}
{% api-method-response-example-description %}
You are hitting rate limits on your TaaS GraphQL endpoint.
{% endapi-method-response-example-description %}

```
Status Code: 429
Retry-After: 58
Content: API calls quota exceeded! maximum admitted 10 per 1m.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
Example of the `GraphQL query object`
{% endhint %}

```graphql
{
  block(block: "884753") {
    protocol
    chain_id
    hash
    header {
      level
      timestamp
    }
  }
}
```

