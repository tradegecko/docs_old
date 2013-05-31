---
layout: developer
category: developer
---
### Setting up the client

To test TradeGecko API, first make sure you have installed the oauth2
gem.

To setup the client, go to your terminal and fire up irb and type:

{% highlight ruby %}
  require 'oauth2'

  client_id     = '...'
  client_secret = '...'
  redirect_uri  = '...'
  site          = "https://api.tradegecko.com"

  client = OAuth2::Client.new(client_id, client_secret, :site => site)
{% endhighlight %}

Now that your client is ready, you can request an authorization code.

### Getting an authorization code

Generate an authorization url with:

{% highlight ruby %}
  client.auth_code.authorize_url(:redirect_uri => redirect_uri)
  # => https://api.tradegecko.com/oauth/authorize?response_type=code&client_id=...&redirect_uri=...
{% endhighlight %}

Go to this url in your browser. You'll see the authorization endpoint.
If you click on Authorize, you'll see a page with the authorization code
in it:

![auth_image](/images/auth.png)

Then you'll get redirected to the redirect uri that you specified along with the code parameter in the query.

      http://my.redirect.uri/callback?code=123456789

With this unique code, you will now be able to request the access token.

### Getting an access token

To request an access token, type:

{% highlight ruby %}
  code = "..." # code you got in the redirect uri
  token = client.auth_code.get_token(code, :redirect_uri => redirect_uri)
  # => <#OAuth2::AccessToken ...>
{% endhighlight %}
You now have access to the TradegGecko API.

### Making your first TradeGecko API request 

{% highlight ruby %}
  response = token.get('accounts')
  JSON.parse(response.body)
  # => { "accounts": [{ "name": "tradegecko", ... }] }
{% endhighlight %}

Congratulations! You just made your first request to the Tradegecko API.

### Request with additional parameters

{% highlight ruby %}
  response = token.post('products') do |request|
    request.params[:product] = {
      name: "Product1",
      description: "My first product"
    }
  end

  JSON.parse(response.body)
  # => {"product"=>{"id"=>22, "name"=>"Product1", "description"=>"My first product", ...} }
{% endhighlight %}


