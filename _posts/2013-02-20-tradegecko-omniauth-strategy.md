---
layout: developer
category: developer
---

In order to provide our users a much better way of accessing our API, we
have created a [Tradegecko strategy](https://github.com/tradegecko/omniauth-tradegecko)
for OmniAuth. [OmniAuth](https://github.com/intridea/omniauth) is a library
that standardizes multi-provider authentication for web applications.

### Usage
In `config/initializers/tradegecko.rb`

{% highlight ruby %}
use OmniAuth::Builder do
  provider :tradegecko, ENV['TRADEGECKO_ID'], ENV['TRADEGECKO_SECRET']
end
{% endhighlight %}

We've provided an example app in
[https://tradegecko-example-app.herokuapp.com/](https://tradegecko-example-app.herokuapp.com/)
 | ([source](https://github.com/tradegecko/tradegecko-example-app))
