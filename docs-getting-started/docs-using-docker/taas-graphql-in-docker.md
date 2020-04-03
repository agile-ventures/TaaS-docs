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
* setting the Tezos:NodeUrl environment variable to [http://172.17.0.1:8732](http://172.17.0.1:8732)

{% hint style="warning" %}
Do not forget to change the **Tezos:NodeUrl** based on your configuration!
{% endhint %}

```bash
docker run --rm -it -p 3000:3000 \
--env TEZOS_NODE="http://172.17.0.1:8732" \
tezoslive/taas-graphql
```

### Optional Configuration

{% hint style="info" %}
By providing the following ENV variables you can override default configuration.
{% endhint %}

```bash
docker run --rm -it -p 3000:3000 \
--env PORT="3000" \
--env TEZOS_NODE="http://172.17.0.1:8732" \
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



