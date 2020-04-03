---
description: WebSocket / SignalR endpoint providing real-time updates
---

# TaaS WebSocket

**Sign in using your GitHub account on** [**TezosLive.io**](https://www.tezoslive.io) **and create your endpoint.**   
  
You don't need to setup or host any server-side or Tezos infrastructure on your side. 

You can also read the [Medium article ](https://medium.com/tezoslive/public-tezos-signalr-websocket-endpoint-available-on-tezoslive-io-28e0dcfcc8f)about the TaaS public endpoint.

{% hint style="danger" %}
**Limitations**

Public SignalR API endpoints are currently limited to

* 20 000 messages per account per day  \(1 message is counted for each 64kB in case message has more than 64kB\)
* 20 concurrent connection per account
{% endhint %}

**For client side instructions** please see

{% page-ref page="../../docs-clients/docs-taas-endpoint-or-function.md" %}



