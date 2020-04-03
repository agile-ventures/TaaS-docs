---
description: GraphQL API interface to Tezos Node RPC API
---

# TaaS GraphQL

**Sign in using your GitHub account on** [**TezosLive.io**](https://www.tezoslive.io) **and create your endpoint.**   
  
You don't need to setup or host any server-side or Tezos infrastructure on your side. 

{% hint style="danger" %}
**Limitations**

Public GraphQL API endpoints are currently limited to

* 1 000 requests per 24 hours
* 10 requests per minute
{% endhint %}

{% hint style="success" %}
Be sure to try out GraphQL playground available at [https://www.tezoslive.io/graphql](https://www.tezoslive.io/graphql)
{% endhint %}

{% hint style="info" %}
If you receive a response from your TaaS GraphQL endpoint with 

**`HTTP 429 status code`**

```text
Status Code: 429
Retry-After: 58
Content: API calls quota exceeded! maximum admitted 10 per 1m.
```

it means you are currently hitting the request rate limits.
{% endhint %}

