# Configure-Splunk-to-pull-Windows-Defender-ATP-alerts


Before you begin
Install the REST API Modular Input app in Splunk.
Make sure you have enabled the SIEM integration feature from the Preferences setup menu. For more information, see Enable SIEM integration in Windows Defender ATP
Have the details file you saved from enabling the SIEM integration feature ready. You'll need to get the following values:
OAuth 2 Token refresh URL
OAuth 2 Client ID
OAuth 2 Client secret
Have the refresh token that you generated from the SIEM integration feature ready.

Configure Splunk
Login in to Splunk.
Click Search & Reporting, then Settings > Data inputs.
Click REST under Local inputs.
NOTE: This input will only appear after you install the REST API Modular Input app.
Click New.
Type the following values in the required fields, then click Save:
NOTE: All other values in the form are optional and can be left blank.
Field
Value
Endpoint URL
Depending on the location of your datacenter, select either the EU or the US URL: 
For EU: https://wdatp-alertexporter-eu.securitycenter.windows.com/api/alerts
For US:https://wdatp-alertexporter-us.securitycenter.windows.com/api/alerts 
HTTP Method
GET
Authentication Type
oauth2
OAuth 2 Access token
Use the value that you generated when you enabled the SIEM integration feature. 
NOTE: The access token expires after an hour. 
OAuth 2 Refresh Token
Use the value that you generated when you enabled the SIEM integration feature.
OAuth 2 Token Refresh URL
Use the value from the details file you saved when you enabled the SIEM integration feature.
OAuth 2 Client ID
Use the value from the details file you saved when you enabled the SIEM integration feature.
OAuth 2 Client Secret
Use the value from the details file you saved when you enabled the SIEM integration feature.
Response type
Json
Response Handler
JSONArrayHandler
Polling Interval
Number of seconds that Splunk will ping the Windows Defender ATP endpoint. Accepted values are in seconds.
Set sourcetype
From list
Source type
_json

After completing these configuration steps, you can go to the Splunk dashboard and run queries.

View alerts using Splunk solution explorer
Use the solution explorer to view alerts in Splunk.

In Splunk, go to Settings > Searchers, reports, and alerts.
Select New.
Enter the following details:
Destination app: Select Search & Reporting (search)
Search name: Enter a name for the query
Search: Enter a query, for example:
source="rest://windows atp alerts"|spath|table*
Other values are optional and can be left with the default values.
Click Save. The query is saved in the list of searches.
Find the query you saved in the list and click Run. The results are displayed based on your query.

Enable SIEM integration in Windows Defender ATP:

https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-atp/enable-siem-integration-windows-defender-advanced-threat-protection

https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-atp/pull-alerts-using-rest-api-windows-defender-advanced-threat-protection
