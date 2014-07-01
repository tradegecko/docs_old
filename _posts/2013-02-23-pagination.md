---
layout: developer
category: developer
---
   The TradeGecko API enables pagination by allowing users to include 'limit'
   and 'page' parameters on GET requests to index pages. The default
   limit is 100 items.

##### Sample request (cURL)

      curl -H "Authorization: Bearer <ACCESS_TOKEN>" https://api.tradegecko.com/users?limit=20&page=1
