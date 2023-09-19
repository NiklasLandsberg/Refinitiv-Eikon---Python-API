# Refinitiv Eikon, Python API
Refinitiv Eikon has a Python API which allows to retrieve stock-related characteristics in a bunch.
The API only works if you have downloaded and logged into the Desktop version of Refinitiv Eikon.
The following link, https://developers.refinitiv.com/en/api-catalog/eikon/eikon-data-api/quick-start, is a neat description of the steps to take in order to get the API to work.

Further, I provide a manual on how you can find and access different kinds of data sets.

1. Open your Refinitiv Eikon Desktop
2. Open your Python IDE
3. Start your script with:
   - import eikon as ek
   - ek.set_app_key("YOUR KEY")
   - ek.set_timeout(x), where x is the timeout you specify.
4. Next go to your Refinitiv Eikon and type **SCREENER** into the search field
5. Specify the relevant universe and your data items.
6. Download the universe as formula and copy and paste the "SCREEN(..)" command into your script.
7. If you want to download data for specific stocks rather than a whole universe of stocks, find the RICs you need and type **DATA ITEM** to the search field.
   There you will find all available data items that you can use for the stocks as well as can verify if particular data items remain **None** after download.

Notes:
1) The universe might error because the retrieval request is too large. For universe settings, e.g. if you want to download **all** stocks, you can use NOT_IN and IN as a workaround. You create two requests where the first request contains all stocks except stocks, e.g. in Germany, and then a second request for stocks only in Germany. Hence, you circumvene the limitation on requests within one call and get all information.
2) I used get_data also for timeseries retrieval because you can access more data items than using timeseries.
3) The RICs (if retrieval for specific stocks), have to be a list of strings that are non-null. Eikon restricts retrieving data for more than 3000-5000 RICS at a time depending on the data items chosen. A work around similar to 1) is to slice the lists into distinct chunks.
