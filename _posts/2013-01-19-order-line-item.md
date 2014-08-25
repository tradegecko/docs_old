---
layout: post
category: api
---

####   Retrieve list of order line items

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/order_line_items/*

##### Sample Response

      {
          "order_line_items": [
              {
                  "discount": null,
                  "freeform": null,
                  "fulfillment_id": 717,
                  "id": 320,
                  "image_url": null,
                  "label": null,
                  "order_id": 99,
                  "position": null,
                  "price": "10.0",
                  "quantity": "1.0",
                  "tax_rate_override": "15.0",
                  "variant_id": 1018
              },
              {
                  "discount": null,
                  "freeform": null,
                  "fulfillment_id": 717,
                  "id": 319,
                  "image_url": "https://images.com/thumbnail.jpeg",
                  "label": null,
                  "order_id": 99,
                  "position": null,
                  "price": "24.0",
                  "quantity": "3.0",
                  "tax_rate_override": "15.0",
                  "variant_id": 1026
              }
          ]
      }

####   Retrieve a specific order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

##### Sample Response

      {
          "order_line_item": {
              "discount": null,
              "freeform": null,
              "fulfillment_id": 717,
              "id": 319,
              "image_url": "https://images.com/thumbnail.jpeg",
              "label": null,
              "order_id": 99,
              "position": null,
              "price": "24.0",
              "quantity": "3.0",
              "tax_rate_override": "15.0",
              "variant_id": 1026
          }
      }

####   Create a new order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/order_line_items/*

##### Sample Response

      {
          "order_line_item": {
              "discount": null,
              "freeform": null,
              "fulfillment_id": 717,
              "id": 319,
              "image_url": "https://images.com/thumbnail.jpeg",
              "label": null,
              "order_id": 99,
              "position": null,
              "price": "24.0",
              "quantity": "3.0",
              "tax_rate_override": "15.0",
              "variant_id": 1026
          }
      }

####   Update an order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the order line item gets updated successfully. 

####   Delete an order line item

######     Request:
Method     | Request URL   
-----------| ------------- 
**DELETE** | *https://api.tradegecko.com/order_line_items/{ORDER_LINE_ITEM_ID}*

###### Return:
      Returns 204 status when the order line item gets deleted successfully. 
