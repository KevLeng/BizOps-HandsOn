
# Lab : Pull Dynatrace data into Excel using Power BI

In this lab is split into two sections, the first section generates an API token request URL we can use the fetch data from Dynatrace. The second section uses this URL to import data into Excel.
If you already have an API token and URL then jump stright to the part of this lab


## Section 1 - Create API Token & Timeseries API Call

### Create API Token

First we need to create a API token.

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click **Generate token**

![Generate Token](/img/gen-token-button.PNG)

2. Enter a name for your token and select the appropriate access switches for the token, then click **Generate**.

In this lab we will only need **Access problem and event feed, metrics and topology**

![Add Token Name](/img/gen-my-token.PNG)

3. Click the down arrow (under the edit column) to display your token. **Take note of the token for later use.**

![Add Token Name](/img/gen-my-token-result.PNG)

### Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click **Dynatrace API Explorer**

Ensure you are using **Environment API** (top right corner of the screen)

2. Click **Authorize**

3. Enter your API token under the DataExportToken (apiKey) and click **Authorise**

![Authorise API with Token](/img/api-auth-key.PNG)

4. Click **Close**

![Authorise API](/img/api-auth.PNG)

### Timeseries API Call 

1. In the API list select **Timeseries**

2. Select **GET /timeseries/{timeseriesIdentifier}**

3. Click **Try it out**

![Tryout Timeseries API](/img/tryout-timeseries-api.PNG)

4. Enter the following paremeters: 

	* timeseriesIdentifier: **com.dynatrace.builtin:app.apdex**
	* includeData: **true**
	* aggregationType: **COUNT**
	* relativeTime: **month**

5. Click **Execute**. If successful the result should be shown looking something like this:

Copy the **Request URL** for use in the next section.

![API Result](/img/api-result.PNG)



## Part 2 - Create API Token & Timeseries API Call

 1. Open Excel and create a new workbook.

 2. Select: **Data > From Web**

 3. Enter your **Request URL** and append **&Api-Token=<your-API-token>**

The URL will look something like this:

https://jlp305.dynatrace-managed.com/e/3afd805d-a30e-42f9-af96-d06b000df230/api/v1/timeseries/com.dynatrace.builtin%3Aapp.apdex?includeData=true&aggregationType=COUNT&relativeTime=month&Api-Token=1234567890

![API Result](/img/excel-import-fromweb.PNG)

 4. In the Power Query Editor window, click on **Record** next to **dataResult**

![API Result](/img/bi-dataresult.PNG)

 5. Click on **Record** next to entities

![API Result](/img/bi-datapoints.PNG)

 6. Click on **List**
 
![API Result](/img/bi-application.PNG)

 7. Click on **To Table**

![API Result](/img/bi-app-to-table.PNG)

 8. Click **OK**

![API Result](/img/bi-to-table.PNG)

Now we have the data in a list but it need to be split and formatted correctly.

 9. Click the icon next to **Column1** and select **Extract Values**

![API Result](/img/bi-extract-values.PNG)

 10 Use **Semicolon** and click **OK**

![API Result](/img/bi-extract-values-semi.PNG)

 11 Right click on **Column1** and select **Split Column** > **By Delimiter...**

![API Result](/img/bi-data-split.PNG)

 12. Use **Semicolon** and **Each occurrence of the delimiter** and click **OK**

![API Result](/img/bi-data-split-delimiter.PNG)

 13. Rename the columns by double clicking on the column name (or right click and select Rename) as follows:
	
	Column1.1 : TimeSpanEPOCH
	Column1.2 : Apdex
	
 14. Add a Custom Column: Click **Add Column**, **Custom Column**
	
![API Result](/img/bi-custom-column.PNG)

 15. Add the following then click **OK**:

	New Column Name : Time
	Custom Column formula : = #datetime(1970, 1, 1, 0, 0, 0) + #duration(0, 0, 0, [TimeSpanEPOCH]/1000)

![API Result](/img/bi-custom-column-config.PNG)

 16. Click the icon next to the Time Column and select *Sort Descending*

![API Result](/img/bi-time-desc.PNG)

 17. Click **Home** > **Close and Load**

![API Result](/img/bi-close-and-load.PNG)


![API Result](/img/excel-initial-data.PNG)
