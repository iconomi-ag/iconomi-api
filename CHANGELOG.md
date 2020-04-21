# Change Log

## 2020 April
  * renamed property "tradeable" to "tradable" in Asset object

## 2020 February 
  * new documentation based on OpenApi v3
  * new /assets endpoints
  * /daa endpoints renamed to /strategies, with old paths still working
  * statistics endpoint for strategies & assets
  * new /user/transaction endpoint
  * add speed type as parameter when posting new structure (only available for institutional customers)
  * add lastRebalanced date on strategy structure endpoint 
  * add monthlyRebalancedCount on strategy structure endpoint
  * new experimental /trading endpoint (ATM only available for institutional customers)
  * add optional granulation parameter to pricing history endpoint
    

## 2019 September 20th: two new endpoints added
  * Submitting a new structure, find it [**here**](https://api.iconomi.com/#tag/REST-API/paths/~1v1~1daa~1{ticker}~1structure/post)
  * Getting the live underlying balances of crypto funds (avaiable only to institutional clients), find it [**here**](https://api.iconomi.com/#tag/REST-API/paths/~1v1~1daa~1{ticker}~1balance/get)

