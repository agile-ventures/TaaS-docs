# /graphql

{% api-method method="post" host="https://www.tezoslive.io" path="/graphql" %}
{% api-method-summary %}
graphql
{% endapi-method-summary %}

{% api-method-description %}
In order to query  the `/graphql` endpoint you need to provide `X-TaaS-Key` in the request.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-TaaS-Key" type="string" required=true %}
Your TaaS GraphQL API endpoint key
{% endapi-method-parameter %}
{% endapi-method-headers %}
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

