# Eikon-API-Data-retrieval
The script in the repository is to systematically retrieve data from Refinitiv`s Python API.

Refinitiv has a Python API which one can access via typing codebook. In the API, you are coding in a Jupiter Notebook that can be downloaded afterwards.

The way how to set up your key and connection is specified in the manual: https://developers.refinitiv.com/en/api-catalog/eikon/eikon-data-api/quick-start
After you got your key, you can access the API.

A manual how to retrieve your data:

1. Go to **CODEBOOK**.
2. Create a new Jupiter Notebook.
3. import eikon as ek and set the key as ek.set_app_key("YOUR KEY")
4. Go to **SCREENER** and specify the relevant universe.
5. Download the universe as formula as you will need the "SCREEN(..)" command.
6. Specify your universe. Note that the universe might have troubles to retrieve data without any NOT_IN or IN constraint. A work around is provided in the code.
7. Go to **DATA ITEM** and search for characteristics you want to retrieve.
8. Specify your field.
9. Retrieve the data and merge the dfs.

If you would like to retrieve a timeseries, a second approach because relevant
10. Specify your time frame.
11. The RIC argument has to be a list with strings and non-null. Eikon has problems to retrieve data for more than 3000-5000 RICS at a time. Hence, you need to slice the lists into chunks.
