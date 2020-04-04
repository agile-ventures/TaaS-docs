# TaaS GraphQL in Docker

## Running TaaS GraphQL in Docker

{% hint style="danger" %}
**Requirements**

* Docker
* Tezos Node with enabled RPC endpoint supporting read-only calls
{% endhint %}

Ready-to-use docker image is available from Docker Hub here: [https://hub.docker.com/r/tezoslive/taas-graphql](https://hub.docker.com/r/tezoslive/taas-graphql).

Example of the `docker run` command

* exposing port 3000
* setting the Tezos:NodeUrl environment variable to [https://api.tezos.org.ua](https://api.tezos.org.ua)

{% hint style="warning" %}
Do not forget to change the **Tezos:NodeUrl** based on your configuration!
{% endhint %}

```bash
docker run --rm -it -p 3000:3000 \
--env TEZOS_NODE="https://api.tezos.org.ua" \
tezoslive/taas-graphql
```

### Optional Configuration

{% hint style="info" %}
By providing the following ENV variables you can override default configuration.
{% endhint %}

```bash
docker run --rm -it -p 3000:3000 \
--env PORT="3000" \
--env TEZOS_NODE="https://api.tezos.org.ua" \
--env MAX_BLOCKS="5" \
--env GRAPHQL_ENABLE_PLAYGROUND="true" \
--env GRAPHQL_ENABLE_INTROSPECTION="true" \
--env ENABLE_API_KEY="true" \
--env API_KEY="random!@#123String" \
tezoslive/taas-graphql
```

* `PORT` configuration for the port on which NodeJS server listens
* `TEZOS_NODE` configuration for the Tezos Node RPC API endpoint
* `MAX_BLOCKS` configuration for the maximum number of blocks that can be fetched using `blocks` GraphQL query
* `GRAPHQL_ENABLE_PLAYGROUND` configuration for the GraphQL playground
* `GRAPHQL_ENABLE_INTROSPECTION` configuration for the GraphQL introspection
* `ENABLE_API_KEY` if enabled API Key is required with each request. API key needs to be provided in the `X-TaaS-Key` header.
* `API_KEY` configures the API key value.

### Testing your GraphQL API endpoint

If you have used default port number \(3000\) and exposed the port using `docker run` command mentioned above, you should be able to access the following URL in the browser \(with enabled `GRAPHQL_ENABLE_PLAYGROUND`\). 

{% embed url="http://127.0.0.1:3000/graphql" caption="Your localhost running Docker" %}

### GraphQL Schema

You can take a look at the schema in the GraphQL playground or on the link below. 

> [https://github.com/agile-ventures/TaaS-GraphQL/blob/master/src/schema/schema.graphql](https://github.com/agile-ventures/TaaS-GraphQL/blob/master/src/schema/schema.graphql)

### Performance & Caching

If you need a caching layer between your GraphQL Docker container and your Tezos Node, you can use TezProxy.

{% embed url="https://github.com/tezexInfo/TezProxy" %}

### Security & Deployment 

For a simple use case you can enable single API key directly on the TaaS GraphQL cointainer with 

* `ENABLE_API_KEY`
* `API_KEY`

If you need more complex solution, like JWT token authentication, rate limiting \(throttling\) or load balancing please take a look at the following resources. 

* [https://www.haproxy.com/blog/using-haproxy-as-an-api-gateway-part-1/](https://www.haproxy.com/blog/using-haproxy-as-an-api-gateway-part-1/)
* [https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-jwt-authentication/](https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-jwt-authentication/)
* [https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-control-access-to-api.html](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-control-access-to-api.html)
* [https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts)

One possible scenario deployed on VMs or dedicated servers could be to have HAProxy load balancer configure with JWT authentication.

  
There are multiple options in case you will opt out to host your TaaS GraphQL stack in the cloud running in the serverless mode \(AWS Lambda, Azure Functions, Cloudflare Workers, etc.\) and the best solution will depend on your specific cloud provider.

