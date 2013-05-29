---
layout: post
category: api
---

####   Retrieve list of stock adjustments

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/stock_adjustments/*

##### Sample Response

      {
          "stock_adjustment_line_items": [
              {
                  "id": 76,
                  "position": 0,
                  "quantity": "-1.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 54725
              }
          ],
          "stock_adjustments": [
              {
                  "adjustment_number": "SA0001",
                  "id": 40,
                  "notes": null,
                  "reason": "damaged",
                  "stock_adjustment_line_item_ids": [
                      76
                  ],
                  "stock_location_id": 159,
                  "updated_at": "2013-05-22T00:22:26Z"
              }
          ]
      }

####   Create a new stock adjustment

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/stock_adjustments/*

##### Sample Response

      {
          "stock_adjustment_line_items": [
              {
                  "id": 76,
                  "position": 0,
                  "quantity": "-1.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 54725
              }
          ],
          "stock_adjustments": {
              "adjustment_number": "SA0001",
              "id": 40,
              "notes": null,
              "reason": "damaged",
              "stock_adjustment_line_item_ids": [
                  76
              ],
              "stock_location_id": 159,
              "updated_at": "2013-05-22T00:22:26Z"
          }
      }
