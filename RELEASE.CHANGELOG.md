### Release 2020-03-03
* **AWS.Logger.Core (1.6.0)**
  * Merge PR [#94](https://github.com/aws/aws-logging-dotnet/pull/94) Added ability to set the ServiceUrl in AWSLoggerConfig to help support using LocalStack. Thanks [Rolf Kristensen](https://github.com/snakefoot).
* **AWS.Logger.AspNetCore (2.2.0)**
  * Updated ILoggingBuilder extension method AddAWSProvider to work with .NET Core 3.X
  * Added support to read ServiceUrl from IConfiguration
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.Log4net (1.5.2)**
  * Added support to read ServiceUrl from AWSAppender
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.NLog (1.5.2)**
  * Added support to read ServiceUrl from AWSTarget
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.SeriLog (1.5.2)**
  * Added support to read ServiceUrl from IConfiguration
  * Update to pull in latest AWS.Logger.Core version


### Release 2019-10-17
* **AWS.Logger.Core (1.5.1)**
  * Merge PR https://github.com/aws/aws-logging-dotnet/pull/96 fixed issue with SendMessages timeout led to Monitor loop break. Thanks [dimmy-timmy](https://github.com/dimmy-timmy)
  * Merge PR https://github.com/aws/aws-logging-dotnet/pull/99 add new DisableLogGroupCreation property to skip creating auto creating Log Group avoiding needing to give IAM permissions to manage Log Group. Thanks [Bart Piotrowski](https://github.com/bartpio)
* **AWS.Logger.AspNetCore (2.1.1)**
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.Log4net (1.5.1)**
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.NLog (1.5.1)**
  * Update to pull in latest AWS.Logger.Core version
* **AWS.Logger.SeriLog (1.5.1)**
  * Update to pull in latest AWS.Logger.Core version

### Release 2019-06-27
* **AWS.Logger.AspNetCore (2.0.0)**
  * New extension methods for ILoggingBuilder to register AWS.Logger.AspNetCore as a log provider.
  * Added support for [Microsoft.Extensions.Logging.ISupportExternalScope](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.logging.isupportexternalscope)
  * Switched default IConfiguration section root to the standard `Logging` root. The library will fallback to the legacy `AWS.Logging` if `LogGroup` is not set in `Logging`.
  * Improve default formatting of log message with new options to include log level, category, event id and exception. View  [README](https://github.com/aws/aws-logging-dotnet#aspnet-core-logging) for more information.
  * Added missing ProfileLocation config setting
  * New config setting for LogStreamNamePrefix
  * Fixed issue with log filtering rules defined in IConfiguration not being evaluated correctly.
  * Updated to version 1.4.0 of AWS.Logger.Core
  * **Note:** Starting with version 2.0.0 this library targets **netstandard2.0** only and references the .NET Core 2.1 version of the Microsoft.Extensions.Logging. The library will work
in newer versions of .NET Core but for versions before .NET Core 2.1 you must use a version before 2.0.0 of AWS.Logger.AspNetCore.
* **AWS.Logger.Core (1.4.0)**
  * Merged PR [#84](https://github.com/aws/aws-logging-dotnet/pull/84) adding support for user defined log stream prefix. Thanks [Bart Piotrowski](https://github.com/bartpio)
  * Updated to latest version of AWSSDK.CloudWatchLogs and AWSSDK.Core to pick up fixes for AWS credential refreshing
* **AWS.Logger.Log4net (1.4.0)**
  * New config property for LogStreamNamePrefix
  * Updated to version 1.4.0 of AWS.Logger.Core
* **AWS.Logger.NLog (1.4.0)**
  * New config property for LogStreamNamePrefix
  * Updated to version 1.4.0 of AWS.Logger.Core
* **AWS.Logger.SeriLog (1.4.0)**
  * Fixed issue [#89](https://github.com/aws/aws-logging-dotnet/issues/89) with appending exception to the end of the message when using JSON formatter causing creating an invalid JSON document.
  * New config setting for Serilog:LogStreamNamePrefix
  * Added missing ProfileLocation config setting
  * Updated to version 1.4.0 of AWS.Logger.Core


### Release 2019-05-15
* **AWS.Logger.NLog (1.3.2)**
    * Merged PR https://github.com/aws/aws-logging-dotnet/pull/71 NLog AWSTarget apply Layout logic to config-properties. Thanks [Rolf Kristensen](https://github.com/snakefoot)

### Release 2018-12-06
* **AWS.Logger.Core (1.3.1)**
    * Merged PR https://github.com/aws/aws-logging-dotnet/pull/53 adding the ability to flush the queued messages. 
Also improving shutdown behavior. Thanks [Rolf Kristensen](https://github.com/snakefoot)
* **AWS.Logger.AspNetCore (1.4.1)**
    * Merged PR https://github.com/aws/aws-logging-dotnet/pull/46 adding support for scopes. Thanks [Stefan Over](https://github.com/Herdo)
    * Bumped dependency of AWS.Logger.Core to 1.3.1
* **AWS.Logger.Log4net (1.3.1)**
    * Merged PR https://github.com/aws/aws-logging-dotnet/pull/59 updating to version 2.0.8 of Log4net. Thanks [Aaron Amm](https://github.com/aaronamm)
    * Merged PR https://github.com/aws/aws-logging-dotnet/pull/59 with new Log4net sample. Thanks [Aaron Amm](https://github.com/aaronamm)
    * Bumped dependency of AWS.Logger.Core to 1.3.1
* **AWS.Logger.NLog (1.3.1)**
    * Bumped dependency of AWS.Logger.Core to 1.3.1
* **AWS.Logger.SeriLog (1.2.1)**
    * Bumped dependency of AWS.Logger.Core to 1.3.1


### Release 2018-07-23
* **AWS.Logger.Core (1.2.0)**
    * Break up large logging messages into sizes that CloudWatch Logs will accept. This change was done to handle the CloudwatchLogs restriction on the event size(256 KB as per https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/cloudwatch_limits_cwl.html). This is addressing the following GitHub issue: https://github.com/aws/aws-logging-dotnet/issues/40
    * Added validation to uphold CloudwatchLogs restriction on the batch size(1 MB as per https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/cloudwatch_limits_cwl.html).
* **AWS.Logger.AspNetCore (1.3.0)**
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.Log4net (1.2.0)**
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.NLog (1.2.0)**
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.SeriLog (1.1.0)**
    * Updated nuspec file with the updated AWS.Logger.Core version
    * Merged in PR https://github.com/aws/aws-logging-dotnet/pull/41 for adding ITextFormatter to format log messages

### Release 2018-02-23
* **AWS.Logger.NLog (1.1.6)**
    * Changed dependency for NetStandard 1.5 from NLog 5 to Nlog 4.5

### Release 2018-02-22
* **AWS.Logger.Core (1.1.7)**
    * Created AssemblyInfo.cs with correct version numbers
* **AWS.Logger.AspNetCore (1.2.6)**
    * Created AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.Log4net (1.1.6)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.NLog (1.1.5)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.SeriLog (1.0.2)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version  


### Release 2018-02-19
* **AWS.Logger.Core (1.1.6)**
* Fixes bug with logger background dying after an arbitrary amount of time. An exception would be thrown and since the catch was outside the main loop, the thread would exit.
* Simplified error handling from main loop
* Simplified main loop method by removing redundant checks
* Cancellation is not an error, and will no longer be logged as such. We were, but not consistently.

### Release 2018-01-04 00:02 UTC
* Modified AssemblyInfo.cs with correct version numbers for all the libraries
* **AWS.Logger.Core (1.1.4)**
    * Modified AssemblyInfo.cs with correct version number
* **AWS.Logger.AspNetCore (1.2.5)**
    * Created AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.Log4net (1.1.5)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.NLog (1.1.4)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version
* **AWS.Logger.SeriLog (1.0.1)**
    * Modified AssemblyInfo.cs with correct version numbers
    * Updated nuspec file with the updated AWS.Logger.Core version  

### Release 2017-12-11 00:02 UTC
* **AWS.Logger.SeriLog (1.0.0)**
    * Added support for SeriLog logging library.
* **AWS.Logger.Log4net (1.1.4)**
    * Added support for Log4net logging library for NetStandard1.5 framework.

### Release 2017-09-28 00:02 UTC
* **AWS.Logger.AspNetCore (1.2.4)**
    * Added exception logging for default ASP.NET Core formatter.

### Release 2017-08-22 00:02 UTC
* **AWS.Logger.AspNetCore (1.2.2)**
    * Fixed issue with **Profile** setting not getting used.

### Release 2017-07-25 10:30 UTC
* **AWS.Logger.Core (1.1.3)**
    * Updated the logic in AWSLoggerCore for creating a logstream. AWSLoggerCore library will try to use the sequence token in the response message of a log PutLogEventsAsync request for a maximum of 5 attempts, before creating a new logstream.
* **AWS.Logger.AspNetCore (1.2.2)**
    * Updated dependency to latest AWS.Logger.Core
* **AWS.Logger.Log4net (1.1.3)**
    * Updated dependency to latest AWS.Logger.Core
* **AWS.Logger.NLog (1.1.3)**
    * Updated dependency to latest AWS.Logger.Core

### Release 2017-06-23 21:30 UTC
* **AWS.Logger.Core (1.1.2)**
    * Pull request [#19](https://github.com/aws/aws-logging-dotnet/pull/19), fixing a NPE. Thanks to [Andrew Kazyrevich](https://github.com/andreister)
* **AWS.Logger.AspNetCore (1.2.1)**
    * Updated dependency to latest AWS.Logger.Core
* **AWS.Logger.Log4net (1.1.2)**
    * Updated dependency to latest AWS.Logger.Core
* **AWS.Logger.NLog (1.1.2)**
    * Updated dependency to latest AWS.Logger.Core

### Release 2017-06-22 21:30 UTC
* **AWS.Logger.AspNetCore (1.2.0)**
    * Pull request [#14](https://github.com/aws/aws-logging-dotnet/pull/14), adding support for custom formatters. Thanks to [Peter Deme](https://github.com/peterdeme).

### Release 2017-05-18 14:30 UTC
* **AWS.Logger.Core (1.1.1)**
    * Added LibraryLogFileName property to log errors encountered by AWSLoggerCore
    * Upgraded library to NetStandard1.5 framework to support System.Runtime.Loader v4.0.0
* **AWS.Logger.AspNetCore (1.1.1)**
    * Added LibraryLogFileName property to log errors encountered by AWSLoggerCore
    * Upgraded library to NetStandard1.5 framework to match AWS.Logger.Core framework
* **AWS.Logger.Log4net (1.1.1)**
    * Added LibraryLogFileName property to log errors encountered by AWSLoggerCore
* **AWS.Logger.NLog (1.1.1)**
    * Added LibraryLogFileName property to log errors encountered by AWSLoggerCore
    * Upgraded library to NetStandard1.5 framework to match AWS.Logger.Core framework
    * Corrected NLog nuspec file to add NLog 4.4.9 for framework v4.5.2
    * Upgraded AWS.Logger.NLog netcore package NLog dependency from v4.4.0-beta5 to 5.0.0-beta07

### Release 2017-05-08 14:30 UTC
* **AWS.Logger.Core (1.1.0)**
    * Added LogStreamNameSuffix property to custom name logStream on CloudWatchLogs
* **AWS.Logger.AspNetCore (1.1.0)**
    * Added LogStreamNameSuffix property to custom name logStream on CloudWatchLogs
* **AWS.Logger.Log4net (1.1.0)**
    * Added LogStreamNameSuffix property to custom name logStream on CloudWatchLogs
* **AWS.Logger.NLog (1.1.0)**
    * Added LogStreamNameSuffix property to custom name logStream on CloudWatchLogs
    * Corrected NLog nuspec file to show dependency on the AWS.Logger.Core

### Release 2016-12-20 09:00 UTC
* **AWS.Logger.Core (1.0.0)**
    * Initial Release
* **AWS.Logger.AspNetCore (1.0.0)**
    * Initial Release
* **AWS.Logger.Log4net (1.0.0)**
    * Initial Release
* **AWS.Logger.NLog (1.0.0)**
    * Initial Release
