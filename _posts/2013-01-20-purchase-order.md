---
layout: post
category: api
---

####   Retrieve list of purchase orders 

######     Request:
Method     | Request URL   
-----------| ------------- 
**GET**    | *https://api.tradegecko.com/purchase_orders/*

##### Sample Response

      {
          "purchase_orders": [
              {
                  "billing_address_id": 153,
                  "company_id": 128,
                  "created_at": "2013-05-08T05:45:57Z",
                  "due_at": "2013-05-22",
                  "email": "carlos@carlsbikes.com",
                  "id": 466,
                  "notes": null,
                  "order_number": "PO0084",
                  "procurement_ids": [],
                  "procurement_status": "unprocured",
                  "purchase_order_line_item_ids": [
                      1928
                  ],
                  "reference_number": null,
                  "status": "active",
                  "stock_location_id": 159,
                  "tax_type": "inclusive",
                  "updated_at": "2013-05-08T05:46:34Z",
                  "vendor_address_id": 188,
                  "xero": "f74d194f-3a96-47de-b783-77114d26d7e9"
              },
              {
                  "billing_address_id": 18,
                  "company_id": 128,
                  "created_at": "2012-11-01T02:09:32Z",
                  "due_at": null,
                  "email": "",
                  "id": 5,
                  "notes": "Thanks Carl for your awesome bike parts",
                  "order_number": "PO0005",
                  "procurement_ids": [],
                  "procurement_status": "unprocured",
                  "purchase_order_line_item_ids": [
                      4,
                      2,
                      3
                  ],
                  "reference_number": "TR00345",
                  "status": "received",
                  "stock_location_id": 18,
                  "tax_type": null,
                  "updated_at": "2013-05-08T03:10:15Z",
                  "vendor_address_id": 188,
                  "xero": null
              },
          ]
      }

####   Retrieve a specific purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/purchase_orders/{PURCHASE_ORDER_ID}*

##### Sample response

      {
          "purchase_order": {
              "billing_address_id": 153,
              "company_id": 103,
              "created_at": "2013-04-30T07:07:13Z",
              "due_at": "2013-05-14",
              "email": "office@mikesbikes.com",
              "id": 412,
              "notes": null,
              "order_number": "PO0082",
              "procurement_ids": [ 249 ],
              "procurement_status": "partial",
              "purchase_order_line_item_ids": [ 1674, 1672, 1671, 1673 ],
              "reference_number": null,
              "status": "active",
              "stock_location_id": 160,
              "tax_type": "inclusive",
              "updated_at": "2013-05-08T03:10:25Z",
              "vendor_address_id": 101,
              "xero": "b5a6d858-3e99-4df5-91e4-e8a01b35828a"
          }
      }

####   Create a new purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**POST**   | *https://api.tradegecko.com/purchase_orders/*

##### Sample Response

      {
          "purchase_order": {
              "billing_address_id": 153,
              "company_id": 103,
              "created_at": "2013-04-30T07:07:13Z",
              "due_at": "2013-05-14",
              "email": "office@mikesbikes.com",
              "id": 412,
              "notes": null,
              "order_number": "PO0082",
              "procurement_ids": [ 249 ],
              "procurement_status": "partial",
              "purchase_order_line_item_ids": [ 1674, 1672, 1671, 1673 ],
              "reference_number": null,
              "status": "active",
              "stock_location_id": 160,
              "tax_type": "inclusive",
              "updated_at": "2013-05-08T03:10:25Z",
              "vendor_address_id": 101,
              "xero": "b5a6d858-3e99-4df5-91e4-e8a01b35828a"
          }
      }

####   Update a purchase order

######     Request:
Method     | Request URL   
-----------| ------------- 
**PUT**    | *https://api.tradegecko.com/purchase_orders/{PURCHASE_ORDER_ID}*

###### Return:
      Returns 204 status when the purchase order gets updated successfully. 
