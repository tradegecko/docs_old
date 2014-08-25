---
layout: post
category: api
---

####   Retrieve list of procurements

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/procurements/*

##### Sample Response

      {
          "procurements": [
              {
                  "created_at": "2013-02-21T23:17:19Z",
                  "id": 51,
                  "purchase_order_id": 127,
                  "purchase_order_line_item_ids": [
                      172
                  ],
                  "received_at": "2013-02-21T23:16:56Z",
                  "updated_at": "2013-02-21T23:17:19Z"
              },
              {
                  "created_at": "2013-01-25T10:43:16Z",
                  "id": 18,
                  "purchase_order_id": 127,
                  "purchase_order_line_item_ids": [
                      175
                  ],
                  "received_at": "2013-01-25T10:43:13Z",
                  "updated_at": "2013-01-25T10:43:16Z"
              }
          ],
          "purchase_order_line_items": [
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 172,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 0,
                  "price": null,
                  "procurement_id": 51,
                  "purchase_order_id": 127,
                  "quantity": "11.0",
                  "tax_rate_override": "15.0",
                  "variant_id": 13410
              },
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 175,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 1,
                  "price": null,
                  "procurement_id": 18,
                  "purchase_order_id": 127,
                  "quantity": "20.0",
                  "tax_rate_override": "15.0",
                  "variant_id": 1996
              }
          ]
      }

####   Retrieve a specific procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/procurements/{PROCUREMENT_ID}*

##### Sample Response

      {
          "procurement": {
              "created_at": "2013-02-21T23:17:19Z",
              "id": 51,
              "purchase_order_id": 127,
              "purchase_order_line_item_ids": [
                  172
              ],
              "received_at": "2013-02-21T23:16:56Z",
              "updated_at": "2013-02-21T23:17:19Z"
          },
          "purchase_order_line_items": [
              {
                  "extra_cost_value": null,
                  "freeform": null,
                  "id": 172,
                  "image_url": "https://images.com/thumbnail__void_0_-16.png",
                  "label": null,
                  "position": 0,
                  "price": null,
                  "procurement_id": 51,
                  "purchase_order_id": 127,
                  "quantity": "11.0",
                  "tax_rate_override": "15.0",
                  "variant_id": 13410
              }
          ]
      }

####   Create a new procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/procurements/*

####   Update a procurement

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/procurements/{PROCUREMENT_ID}*

###### Return:
      Returns 204 status when the procurement gets updated successfully. 
