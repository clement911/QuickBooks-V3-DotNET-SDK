[![SDK Banner](views/SDK.png)][ss1]

V3-DotNet-SDK
=============
<p align="center">
    <img src="./os-project-logo.svg" width="150" alt="Logo"/>
</p>
IDG .NET SDK for QuickBooks V3
(Class lib Project written in .NET Standard 2.0- Supports .Net Full Framework 4.6.1, 4.7.2 and .Net Core 2.1,.Net Core 2.2)

**Support:** [![Help](https://img.shields.io/badge/Support-Intuit%20Developer-blue.svg)](https://help.developer.intuit.com/s/) <br/>
**Documentation:** [![User Guide](https://img.shields.io/badge/User%20Guide-SDK%20docs-blue.svg)](https://developer.intuit.com/app/developer/qbo/docs/develop/sdks-and-samples-collections/net) [![Refer SDK class lib docs](https://img.shields.io/badge/Class%20Lib%20Docs-.Net%20SDK-blue.svg)](https://developer-static.intuit.com/SDKDocs/QBV3Doc/IPPDotNetDevKitV3/html/5ca993d2-af77-d050-e246-681e5983b440.htm)<br/>
**License:** [![Apache 2](http://img.shields.io/badge/license-Apache%202-brightgreen.svg)](http://www.apache.org/licenses/LICENSE-2.0) <br/>
**Binaries:** [![Nuget](https://img.shields.io/badge/Nuget-14.4.0.0-blue.svg)](https://www.nuget.org/packages/IppDotNetSdkForQuickBooksApiV3)<br/>
**Binaries for OAuth2 only:** [![Nuget](https://img.shields.io/badge/Nuget-14.0.0.0-blue.svg)](https://www.nuget.org/packages/IppOAuth2PlatformSdk)<br/>


The QuickBooks Online .NET SDK provides a set of .NET class libraries that make it easier to call QuickBooks Online APIs, and access to QuickBooks Online data. It supports .Net Core 2.1, .Net Core 2.2, .Net Full Framework 4.6.1 and 4.7.2. Some of the features included in this SDK are:

* Ability to perform single and batch processing of CRUD operations on all QuickBooks Online entities.
* A common interface to the Request and Response Handler with two implemented classes to handle both synchronous and asynchronous requests.
* Support for both XML and JSON Request and Response formats.
* Ability to configure app settings in the configuration file requiring no additional code change.
* Support for Gzip and Deflate compression formats to improve performance of Service calls to QuickBooks Online.
* Retry policy constructors to help apps handle transient errors.
* Logging mechanisms for trace and request/response logging.
* Query Filters that enable you to write Intuit queries to retrieve QuickBooks Online entities whose properties meet a specified criteria.
* Queries for accessing QuickBooks Reports.
* Sparse Update to update writable properties specified in a request and leave the others unchanged.
* Change data that enables you to retrieve a list of entities modified during specified time points.
* Supports OAuth2

Note: 
->Oauth1 support has been removed from this SDK. Intuit.Ipp.Retry logic now have been moved to Intuit.Ipp.Core. So, if you see Retry not found issues while updating your code, just remove that Using Intuit.Ipp.Retry statement and add Using Intuit.Ipp.Core if not already present.

**Understanding the .Net SDK code structure:**

**Schema**
* [Schema](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Tools/XsdExtension/Intuit.Ipp.XsdExtension/Schema) - Schema files for QBO V3 APIs are available under this folder.

The code has been divided into following main categories-

**Data projects**
* [Intuit.Ipp.XsdExtension](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Tools/XsdExtension/Intuit.Ipp.XsdExtension) - This is an external tool whose executable is used to generate the different classes based on the input QBO V3 service schema. 

* [Intuit.Ipp.Data](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Tools/XsdExtension/Intuit.Ipp.Data/) - This project has the updated classes in CDMEntities folder generated by the XsdExtension tool based on new releases of schema.


**Core and Common functionality projects**
* [Intuit.Ipp.Core](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Core) - This project does the job of handling the core functionalities like handling configuration, handling sync, async requests, callbacks and retry logic.

* [Intuit.Ipp.QueryFilter](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.QueryFilter) - Handles all query operations related logic.

* [Intuit.Ipp.Utility](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Utility) - Handles serialization, deserialization logic, compression, and other config based logic for the API calls.

* [Intuit.Ipp.Diagnostics](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Diagnostics) - Handles the old Trace Logger code.

* [Intuit.Ipp.Exception](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Exception) - Handles the exception logic for the different services calls. 


**Service projects**
* [Intuit.Ipp.DataService](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.DataService) - Handles all the Namelist and Transaction entities related operations for sync, async modes and batch mode.

* [Intuit.Ipp.EntitlementService](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.EntitlementService)- Handles Entitlement API related operations. It supports XML request -response format only.

* [Intuit.Ipp.GlobalTaxService](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.GlobalTaxService) - Handles the custom tax creation related operations. It supports JSON API request- response format only.

* [Intuit.Ipp.ReportService](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.ReportService) - Handles all the Reports endpoints related operations

* [Intuit.Ipp.WebHooksService](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.WebHooksService) - Handles the Webhooks related logic.


**Security/Auth related projects**
* [Intuit.Ipp.OAuth2PlatformClient](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.OAuth2PlatformClient) - Handles OAuth2 related API calls

* [Intuit.Ipp.Security](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Security) - Generates the Authorization header for the API calls 

**Test Projects**
* Unit Tests - All unit test projects are available under the [Code](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code) folder. You can identify them if they have a .Test suffix in their name.
* Integration Tests -  All integration tests are available under [Intuit.Ipp.Test](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Test/Intuit.Ipp.Test)

**Nuget Package Creation Project**
* [Intuit.Ipp.Nupkg](https://github.com/intuit/QuickBooks-V3-DotNET-SDK/tree/master/IPPDotNetDevKitCSV3/Code/Intuit.Ipp.Nupkg)- This project has the configuration for version of package and all dependencies.After you do a build in Release mode, this project will generate the Nuget packages under the folder Code->artifacts->nupkg for the different .Net supported versions listed above. You can then upload the package to a Nuget org.


**Understanding some important exceptions thrown by the SDK**
* **IdsException** - This is the base execption thrown when other sub exceptions cannot catch it. Make sure to enable logs to get details for the internal error when you see this exception. These may be related to service downtime.
* **ValidationException** - These are valid business validation rules based error and should be corrected in the code. These are all API related exceptions,
* **InvalidTokenException** - This exception is thrown when your OAuth2 token has expired or is invalid. You will need to regenerate a new token by doing OAuth2 again or renew you tokens if they are still valid.


## Enabling logs for the SDK
Logs help you in easliy identifying detailed issues with your payload, get more info in the exception details for fixing them.
* New logging support was added to the SDK which includes support for reporting headers and multiple logging sinks available from Serilog. You can chooise to have either one or more of these logging sinks enabled. -
Serilogger logs can be enabled for **OAuth2PlatformClient** using the following lines -

            static OAuth2Client oauthClient = new OAuth2Client(clientID, clientSecret, redirectURI, appEnvironment);
            //Use this line to enable only intuit-tid based logs, no tokens/response will be logged. 
            //If set to false, all detailed logs will be available for response
            //If set to true, only intuit-tid response headers will be available
            oauthClient.EnableAdvancedLoggerInfoMode = true;
            oauthClient.EnableSerilogRequestResponseLoggingForConsole = true;
            oauthClient.EnableSerilogRequestResponseLoggingForDebug = true;
            oauthClient.EnableSerilogRequestResponseLoggingForRollingFile = true;
            oauthClient.EnableSerilogRequestResponseLoggingForTrace = true;
            oauthClient.ServiceRequestLoggingLocationForFile = @"C:\Documents\Serilog_log";//Any drive logging location
            
            
Serilogger logs can be enabled for **QBO API calls** using the following lines -

            ServiceContext context = new ServiceContext(dictionary["realmId"], IntuitServicesType.QBO, oauthValidator);

            context.IppConfiguration.AdvancedLogger.RequestAdvancedLog.EnableSerilogRequestResponseLoggingForRollingFile = true;
            context.IppConfiguration.AdvancedLogger.RequestAdvancedLog.EnableSerilogRequestResponseLoggingForConsole = true;
            context.IppConfiguration.AdvancedLogger.RequestAdvancedLog.EnableSerilogRequestResponseLoggingForTrace = true;
            context.IppConfiguration.AdvancedLogger.RequestAdvancedLog.EnableSerilogRequestResponseLoggingForDebug = true;
            context.IppConfiguration.AdvancedLogger.RequestAdvancedLog.ServiceRequestLoggingLocationForFile = @"C:\Documents\Serilog_log"; //Any drive logging location
            
Old file based logs can be enabled by using the following lines-
 
            context.IppConfiguration.Logger.RequestLog.EnableRequestResponseLogging = true;
            context.IppConfiguration.Logger.RequestLog.ServiceRequestLoggingLocation = @"C:\Documents\Serilog_log"; //Any drive logging location
            
* **Fiddler logs are really useful too. You can enable them by following the steps below**

Download Fiddler from Google and run it alongside your code to log raw requests and responses along with URL and headers.
When you download Fiddler, open it, go to Tools > Fiddler Option > Enable (Tick Mark) Capture HTTPS connects > Enable Decrypt Https traffic. That’s it. No other setting is required. The .NET localhost is by default captured in Fiddler, so after you have enabled https traffic in Fiddler just run your code. (Fiddler should be open.) You will see requests and responses logged in Fiddler.
You should set 'decode the raw request body' by clicking on the yellow bar in Fiddler. Then go to the File menu on top, select Save all session > Save the fiddler session. A .saz file is created, which can be viewed later.


## Running Tests

Refer to the following steps to generate all the keys required to run tests using OAuth Playground-
  
* Go to [Developer Docs](https://developer.intuit.com/). 
* Create an app on our IDG platform for the QuickBooks Online v3 APIs. 
* For OAuth2 apps, you will get a set of Development keys, including client key and client secret. This can be used to get OAuth access token and refresh token for sandbox companies.  

* To get Prod app keys to get OAuth tokens for live companies: Go to your app->Settings tab-> enter all URLs and save. Then get the prod keys from Keys tab under Prod section. 
* To get OAuth access tokens, go to your app's dashboard, Click `Oauth Playground`
    * For OAuth2 apps, select the desired app and make sure the OAuth playground redirect_uri is present under Keys tab and go through the OAuth authorization flow to get access and refresh tokens along with the realmid to make API calls for QuickBooks company. 
      * Access tokens are valid for 1 hour which can be refreshed using refesh token. When you request a fresh access token, always use the refresh token returned in the most recent refreshing access token API response. A refresh token expires 24 hours after you receive it. More info can be found at: [Refreshing the access token](https://developer.intuit.com/docs/00_quickbooks_online/2_build/10_authentication_and_authorization/10_oauth_2.0#/Refreshing_the_access_token)
 

 * NOTE: For sandbox testing, you need to use dev app keys and sandbox base URL. 
For live/prod QuickBooks company testing, use prod app keys and prod base URL after doing a private publish as mentioned below. 
Go to your app->Prod tab-> enter all URLs and save. Then get the prod keys from Keys tab under Prod tab of the app. 



## Contribute:
We greatly encourage contributions! You can add new features, report and fix existing bugs, write docs and
tutorials, or any of the above. Feel free to open issues and/or send pull requests.

The `master` branch of this repository contains the latest release of the SDK, while snapshots are published to the `develop` branch. In general, pull requests should be submitted against `develop` by forking this repo into your account, developing and testing your changes, and creating pull requests to request merges. See the [Contributing to a Project](https://guides.github.com/activities/contributing-to-open-source/)
article for more details about how to contribute.

Steps to contribute:

1. Fork this repository into your account on Github
2. Clone *your forked repository* (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/QuickBooks-V3-DotNET-SDK.git`
3. Design and develop your changes
4. Add/update unit tests
5. Create a pull request for review to request merge
6. Obtain approval before your changes can be merged

Note: Before you submit the pull request, make sure to remove the keys and tokens from appsettings.json

Thank you for your contribution!

[ss1]: https://help.developer.intuit.com/s/SDKFeedback?cid=1155




