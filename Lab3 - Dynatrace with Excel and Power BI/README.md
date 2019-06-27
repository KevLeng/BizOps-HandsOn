
# Lab 3: Pull Dynatrace data into Excel using Power BI

In this lab is split into two parts, the first section generates an API token request URL we can use the fetch data from Dynatrace. The second part uses thius URL to import data into Excel.
If you already have an API token and URL then jump stright to the part of this lab


## Part 1 - Create API Token & Timeseries API Call

### Create API Token

First we need to create a API token.

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click Generate token button

![Generate Token](/img/gen-token-button.PNG)

2. Enter a name for your token and select the appropriate access switches for the token, then click **Generate**.

In this lab we will only need "Access problem and event feed, metrics and topology"

![Add Token Name](/img/gen-my-token.PNG)

3. Click the down arrow (under the edit column) to display your token. **Take note of the token for later use.**

![Add Token Name](/img/gen-my-token-result.PNG)

### Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click **Dynatrace API Explorer**

2. Click **Authorize**

3. Enter your API token under the DataExportToken (apiKey) and click **Authorise**

![Authorise API](/img/api-auth.PNG)

4. Click **Close**


### Timeseries API Call 

1. In the API list select **Timeseries**

2. Select **GET /timeseries/{timeseriesIdentifier}**

3. Click **Try it out**

![Tryout Timeseries API](/img/tryout-timeseries-api.PNG)

4. Enter the following paremeters: 

	timeseriesIdentifier: **com.dynatrace.builtin:app.apdex**
	includeData: **true**
	aggregationType: **COUNT**
	reletiveTime: **month**
	Tag (array):  **easytravel**

5. Click **Execute**. If sucessful the result should be shown looking something like this:

![API Result](/img/api-result.PNG)

## Part 2 - Create API Token & Timeseries API Call

