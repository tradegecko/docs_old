---
layout: developer
category: developer
---
   The TradeGecko API is entirely JSON based. In order to make an authenticated call
   to the API, you must include your access token with the call.
   OAuth2 uses a BEARER token that is passed along in an Authorization
   header.

##### Sample request (cURL)

      curl -H "Authorization: Bearer <ACCESS_TOKEN>" http://api.tradegecko.com/accounts
