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
**POST**   | *https://api.tradegecko.com/stock_adjustments*

######     Arguments:
      adjustment_number: 
        A unique identifer. Will be auto-generated if not provided. See https://api.tradegecko.com/stock_adjustments/available_identifiers 
      notes: optional
      reason: required
        Category the adjustment falls under. E.g. "supplier", "customer, "damaged", "shrinkage", "promotion"
      stock_adjustment_line_items: optional
        You can optionally include line items in the create request.
      stock_location_id: required
        The id of the stock location from where this stock is being updated

##### Sample Request
      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>" 
      https://api.tradegecko.com/stock_adjustments/ -d '{
        "stock_adjustment": {
          "adjustment_number": "SA0001",
          "notes": "EOY 2013 Stocktake",
          "reason": "shrinkage",
          "stock_location_id": 17003, 
          "stock_adjustment_line_items": [
            { 
              "quantity": -10, 
              "variant_id": 83375
            },
              "quantity": 5, 
              "variant_id": 83376
            { 
            }
          ],
        }
        }'

##### Sample Response

      {
          "stock_adjustment_line_items": [
              {
                  "id": 76,
                  "position": 0,
                  "quantity": "-10.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 83375
              },
              {
                  "id": 77,
                  "position": 0,
                  "quantity": "5.0",
                  "stock_adjustment_id": 40,
                  "variant_id": 83376
              }
          ],
          "stock_adjustments": {
              "adjustment_number": "SA0001",
              "id": 40,
              "notes": "EOY 2013 Stocktake",
              "reason": "shrinkage",
              "stock_adjustment_line_item_ids": [
                  76,
                  77
              ],
              "stock_location_id": 17003, 
              "updated_at": "2013-05-22T00:22:26Z"
          }
      }
