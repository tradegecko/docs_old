---
layout: post
category: api
---

This is an object representing a tax_component.

Attribute                      | Type          | Description
------------------------------ | ------------- | ------------
**id**                         | Integer       |  A unique identifier for the tax_component
**tax_type_id**                | Integer       |  ID of the parent tax_type
**position**                   | Integer       |
**label**                      | String        |  Display name
**rate**                       | Integer       |  Tax Rate
**compound**                   | Boolean       |

####   Retrieve list of tax_components

######     Request:
Method     | Request URL
-----------| -------------
**GET**    | *https://api.tradegecko.com/tax_components/*

##### Sample Response

      {
        tax_components: [
          {
              id: 39445,
              tax_type_id: 39051,
              position: 0,
              label: "retail",
              rate: "15.0",
              compound: false
          },
          {
              id: 38093,
              tax_type_id: 37704,
              position: 0,
              label: "State",
              rate: "10.0",
              compound: false
          },
          {
              id: 38094,
              tax_type_id: 37704,
              position: 1,
              label: "CND",
              rate: "2.0",
              compound: false
          },
        ]
      }

####   Retrieve a specific tax_component

######     Request:
Method     | Request URL
-----------| -------------
**GET**    | *https://api.tradegecko.com/tax_components/{TAX_COMPONENT_ID}*

##### Sample Response

      {
          tax_component: {
              id: 39445,
              tax_type_id: 39051,
              position: 0,
              label: "retail",
              rate: "15.0",
              compound: false
          },
      }

####   Create a new tax_component

######     Request:
Method     | Request URL
-----------| -------------
**POST**   | *https://api.tradegecko.com/tax_components/*

##### TaxComponent Attributes

Attribute                      | Type          | Description                | Required
------------------------------ | ------------- | -------------------------- | ------------
**tax_type_id**                | Integer       |  ID of the parent tax_type |
**position**                   | Integer       |                            |
**label**                      | String        |  Display name              | True
**rate**                       | Integer       |  Tax Rate                  | True
**compound**                   | Boolean       |                            |


##### Sample Request

      curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer 5cebde19ceae0414c10ea604de05b64cf1ee39f35d503f746601c1dfa89dcbcb" \
      -d "{\"tax_component\":{\"compound\":true,\"label\":\"retail\",\"position\":1,\"rate\":12,\"tax_type_id\":1}}"
      http://api.lvh.me:3000/tax_components

##### Sample Response

      {
          tax_components: {
              id: 39445,
              tax_type_id: 39051,
              position: 0,
              label: "retail",
              rate: "15.0",
              compound: false
          },
      }

####   Update a new tax_component

######     Request:
Method     | Request URL
-----------| -------------
**POST**   | *https://api.tradegecko.com/tax_components/{TAX_COMPONENT_ID}*

##### TaxComponent Attributes

Attribute                      | Type          | Description
------------------------------ | ------------- | ------------
**tax_type_id**                | Integer       |  ID of the parent tax_type
**position**                   | Integer       |
**label**                      | String        |  Display name
**rate**                       | Integer       |  Tax Rate
**compound**                   | Boolean       |

##### Sample Request

      curl -X PUT -H "Content-type: application/json" -H "Authorization: Bearer 5cebde19ceae0414c10ea604de05b64cf1ee39f35d503f746601c1dfa89dcbcb" \
      -d "{\"tax_component\":{\"compound\":true,\"label\":\"retail\",\"position\":1,\"rate\":12,\"tax_type_id\":1}}"
      http://api.lvh.me:3000/tax_components/{TAX_COMPONENT_ID}*

##### Sample Response

      {
          tax_components: {
              id: 39445,
              tax_type_id: 39051,
              position: 0,
              label: "retail",
              rate: "15.0",
              compound: false
          },
      }



####   Delete a tax_component

######     Request:
Method     | Request URL
-----------| -------------
**DELETE**    | *https://api.tradegecko.com/tax_components/{TAX_COMPONENT_ID}*

###### Return:
      Returns 204 status when the tax_component gets deleted successfully.
