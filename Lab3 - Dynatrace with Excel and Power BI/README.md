
# Lab 3: Pull Dynatrace data into Excel using Power BI

In this lab, we will pull data into Excel from Dynatrace. We are going to use Dynatrace API's and Power BI with Excel.

## Create API Token

First we need to create a API token.

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click Generate token button

![Generate Token](/img/gen-token-button.PNG)

2. Enter a name for your token and select the appropriate access switches for the token, then click **Generate**.

In this lab we will only need "Access problem and event feed, metrics and topology"

![Add Token Name](/img/gen-my-token.PNG)

3. Click the down arrow (under the edit column) to display your token. Note the token down for later use.

![Add Token Name](/img/gen-my-token-result.PNG)

## Access API Explorer

In the Dynatrace dashboard, navigate to the Configuration API: **Settings -> Integration -> Dynatrace API**

1. Click **Dynatrace API Explorer**

2. Click **Authorize**

3. Enter your API token under the DataExportToken (apiKey) and click **Authorise**

![Authorise API](/img/api-auth.PNG)

4. Click **Close**


## Timeseries API Call 

1. In the API list select **Timeseries**

2. Select **GET /timeseries/{timeseriesIdentifier}**

3. Click **Try it out**

![Tryout Timeseries API](/img/tryout-timeseries-api.PNG)



4. Modify the Exercise 1 – AgentInstall.bat file (found on the desktop) with the appropriate information. The appropriate info can be found in the intall.bat file contained in the MSI package.

You need to collect **token** & **token** from the install.bat and populate in the Exercise 1 – AgentInstall.bat file

Also, you'll need to change the file name referenced to the version of the MSI you have downloaded.

Copy the OneAgent MSI file to C:\