---
layout: developer
category: developer
---

**Important: Do not disclose your Privileged Access Tokens to anyone else.**

You can now generate Privileged Access Tokens to be used for accessing the TradeGecko API.
These keys do not have an expiry which means that you can access the API using the privileged token
without the need for a refresh token. In any case that your privileged key gets compromised, you should
immediately revoke them through the [TradeGecko App List](https://go.tradegecko.com/oauth/applications).


Once you have obtained your Privileged Access Token, you can use cURL to check if it is working.
{% highlight bash %}
curl -H "Authorization: Bearer <ACCESS_TOKEN>" https://api.tradegecko.com/accounts
{% endhighlight %}
