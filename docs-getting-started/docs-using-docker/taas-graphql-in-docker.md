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
tezoslive/taas-graphql
```

* `PORT` configuration for the port on which NodeJS server listens
* `TEZOS_NODE` configuration for the Tezos Node RPC API endpoint
* `MAX_BLOCKS` configuration for the maximum number of blocks that can be fetched using `blocks` GraphQL query
* `GRAPHQL_ENABLE_PLAYGROUND` configuration for the GraphQL playground
* `GRAPHQL_ENABLE_INTROSPECTION` configuration for the GraphQL introspection

### Testing your GraphQL API endpoint

If you have used default port number \(3000\) and exposed the port using `docker run` command mentioned above you should be able to access the following URL in the browser \(with enabled `GRAPHQL_ENABLE_PLAYGROUND`\). 

{% embed url="http://127.0.0.1:3000/graphql" caption="Your localhost running Docker" %}



