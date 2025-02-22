---
Order: 10
xref: ccm-release-notes
Title: Release Notes
Description: Release Notes for Chocolatey Central Management
RedirectFrom: docs/release-notes-central-management
---

# Chocolatey Release Notes - Chocolatey Central Management
## Summary
This covers the release notes for the Chocolatey Central Management (`chocolatey-management-database`, `chocolatey-management-service`, and `chocolatey-management-web`) packages, which covers Central Management server-side functionality. For more information, installation options, etc, please refer to [Chocolatey Central Management](xref:central-management).

* Installation - [Central Management Setup](xref:ccm-setup)
* Upgrade - [Central Management Upgrade](xref:ccm-upgrade)

> :memo: **NOTE**
>
> This package is available to Chocolatey for Business (C4B) customers only.

## Other Release Notes
* Refer to [Open Source Release Notes](xref:floss-release-notes) as commercial editions build on top of open source.
* Chocolatey for Business (C4B) customers - also refer to [Chocolatey Licensed Extension Release Notes](xref:licensed-extension-release-notes) and [Chocolatey Agent Release Notes](xref:agent-release-notes).

## Known Issues
* Please see https://github.com/chocolatey/chocolatey-licensed-issues/labels/CentralManagement
* Some issues may be held internally, please follow your support routes to learn more.

## 0.6.3 (September 23rd, 2021)
### BUG FIXES
 * Fix - Processing of message queue does not complete when an invalid XML file is located - see [Licensed #266](https://github.com/chocolatey/chocolatey-licensed-issues/issues/266)
 * Fix - When the "Only one concurrent login per user" setting is enabled, users are locked out of CCM Web UI - see [Licensed #260](https://github.com/chocolatey/chocolatey-licensed-issues/issues/260)
 * Fix - Error shown when navigating to certain pages within the CCM Web UI - see [Licensed #262](https://github.com/chocolatey/chocolatey-licensed-issues/issues/262)
 * Fix - Users are unable to change IsOutdated status for software entries within CCM Web UI - see [Licensed #264](https://github.com/chocolatey/chocolatey-licensed-issues/issues/264)
 * Fix - Users are unable to delete a piece of software within CCM Web UI - see [Licensed #261](https://github.com/chocolatey/chocolatey-licensed-issues/issues/261)
 * Fix - Incorrect total number of affected instances within Outdated Software Details Report Details - see [Licensed #265](https://github.com/chocolatey/chocolatey-licensed-issues/issues/265)


## 0.6.2 (August 26th, 2021)
### BUG FIXES
 * Fix - Service - Method to determine correct SSL certificate to use between CCM Service installation script and execution is inconsistent
 * Fix - Service - Exceptions thrown during CCM Service startup do not halt internal service tasks
 * Fix - Service - CCM Service log file does not contain full error information - see [Licensed #247](https://github.com/chocolatey/chocolatey-licensed-issues/issues/247)
 * Fix - Service - Unnecessary/unhelpful log messages are added to the CCM Service log file
 * Fix - Web - Upgrading CCM Website package doesn't complete successfully due to locked files
 * Fix - Web - Upgrading CCM Website package doesn't ensure creation of required configuration in appsettings.json file
 * Fix - Web - Upgrading CCM Website package doesn't ensure creation of required configuration in web.config file
 * Fix - Web - Unable to "see" newly created Outdated Software Report when there are greater than 10 reports
 * Fix - Web - Incorrect total number of Outdated Software Reports displayed
 * Fix - Database - Unable to install 0.6.0/0.6.1 database package when IIS is not installed - see [Licensed #248](https://github.com/chocolatey/chocolatey-licensed-issues/issues/248)

## 0.6.1 (August 5th, 2021)
### BUG FIXES
 * Fix - Service - Unable to install chocolatey-management-service package under certain conditions - see [Licensed #242](https://github.com/chocolatey/chocolatey-licensed-issues/issues/242)

## 0.6.0 (August 3rd, 2021)
### BREAKING CHANGES
 * Audit Retention
   * By default, Audit Logs generated within CCM will now be kept for 30 days, after which they will be removed
   * This can be [changed](https://docs.chocolatey.org/en-us/central-management/setup/website#step-4.5-audit-retention) within the Administration | Settings screen of the CCM Web Application
   * If you wish to retain all your current audit logs, we recommend that you back up the AbpAuditLogs table prior to upgrading to this release

### ENHANCEMENTS
 * All CCM Components have been updated to use .NET Core 3.1 which is supported until [December 2022](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Previous versions of CCM used NET Core 2.2 which Microsoft ended support for in [December 2019](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)
 * Due to this update, the CCM Website now uses the in-process hosting model within IIS. This is enabled by [default starting with ASP.NET Core 3.0](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/iis/in-process-hosting?view=aspnetcore-5.0#enable-in-process-hosting).

## 0.5.1 (April 12th, 2021)
### BUG FIXES
 * Fix - Service - Unable to process deployment report messages that contain invalid XML characters - see [Licensed #216](https://github.com/chocolatey/chocolatey-licensed-issues/issues/216)

### Release Video

A short video explaining what is included in this release can be found here:

<p>
<div class="ratio ratio-16x9">
    <iframe src="https://www.youtube.com/embed/ED6vAz6_AHk?list=PL84yg23i9GBilzTYltuVSvxuqPg56cCCe" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>
    </iframe>
</div>
<br>
</p>

## 0.5.0 (March 25, 2021)
### BREAKING CHANGES
 * Deployments - Provide better resiliency when handling large numbers of computers within a deployment - see [Licensed #212](https://github.com/chocolatey/chocolatey-licensed-issues/issues/212)

Previously, while not recommended, the CCM Service could be run as a user with non-administrative rights on the machine, as long as certain permissions were provided to the user.  Going forward, there is now a strict requirement that the user that is running the CCM Service has administrative rights on the machine.  This is needed to ensure reliability of messages delivered into the CCM Service.

### BUG FIXES
 * Fix - Web - No data is returned when logged into the website with FIPS compliant checksums enabled on the hosting server - see [Licensed #167](https://github.com/chocolatey/chocolatey-licensed-issues/issues/167)

### IMPROVEMENTS
 * Installation - CCM Chocolatey Package scripts have been authenticode signed

### Release Video

A short video explaining what is included in this release can be found here:

<p>
<div class="ratio ratio-16x9">
    <iframe src="https://www.youtube.com/embed/ZeT4NxNRFwg?list=PL84yg23i9GBilzTYltuVSvxuqPg56cCCe" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen>
    </iframe>
</div>
<br>
</p>

## 0.4.0 (November 6, 2020)
### BREAKING CHANGES
 * Deployments - Machine contact timeout now defaults to infinite (0) to allow for semi-connected environments

Previously this value was set to a constant value of 20 and not configurable. To revert to previous behaviour, set the machine contact timeout in minutes value for a given deployment step to 20.

### FEATURES
 * Deployment Scheduling
   * Scheduled Deployments allows for starting a deployment at some point in the future
   * Maintenance Windows - Ability to specify date and time for when no more computers within a deployment can start
 * API - Swagger UI allows visualization and interaction with all CCM API operations - see [Licensed #183](https://github.com/chocolatey/chocolatey-licensed-issues/issues/183)
 * Long Running Deployments - Enables support for semi-connected computers

### BUG FIXES
 * Fix - Deployments - Computers marked unreachable should not be picked up in future steps in same deployment
 * Fix - Deployments - Adding distinct groups that share computers to a deployment results in duplicated computers within deployment steps
 * Fix - Web - Authentication of external user (i.e. LDAP) fails when no email address is configured for user - see [Licensed #181](https://github.com/chocolatey/chocolatey-licensed-issues/issues/181)
 * Fix - Database - Unable to upgrade database when user specific permissions (i.e. instead of assigning a role to a user) for CCM are used for any user
 * Fix - Deployments - Execution timeout of infinite (0) for a deployment step is not being respected when querying for timed out computers
 * Fix - Deployments - Machine contact timeout for deployment step is not being respected, deployments incorrectly wait indefinitely (due to changes in v0.3.1)
 * Fix - Web - Real time notifications never reach CCM Web UI
 * Fix - Web - Notifications page has no way to see entire notification

### IMPROVEMENTS
 * Deployments - Handle deployment step activation order properly when the same computer is in multiple deployments that are active at the same time
 * Service - Configuration - Provide clarity in log messages when salt additive configuration values are misconfigured
 * Deployments - Round percentage complete values on report pages while deployment is in progress
 * Deployments - Auto-refresh deployment report pages


## 0.3.1 (October 5, 2020)
### BUG FIXES
 * Fix - Database - Upgrade fails when passing database parameters due to incorrect cmdlet name - see [Licensed #161](https://github.com/chocolatey/chocolatey-licensed-issues/issues/161)
 * Fix - Service Install - Ensure that existing certificate is located in TrustedPeople certificate store
 * Fix - Service Install - Netsh Entries Incorrectly Parsed ("Cannot index into a null array") when installing in different locales - see [Licensed #174](https://github.com/chocolatey/chocolatey-licensed-issues/issues/174)
 * Fix - Web - Invalid LDAP credentials/URL should not prevent login for ccmadmin user
 * Fix - Deployments - Start Date Time for Deployment Step is overwritten when Step is marked as inconclusive
 * Fix - Deployments - Switching from Basic to Advanced script without providing package name causes validation errors - see [Licensed #164](https://github.com/chocolatey/chocolatey-licensed-issues/issues/164)

### IMPROVEMENTS
 * Service Install - Allow skipping certificate binding with package parameter /SkipCertificateBinding
 * Include CreationTime property on Deployment Plan entity - useful when querying via CCM API
 * Web - Deployments UI - Add Deployment Step modal window should default to basic view

## 0.3.0 (June 25, 2020)
### BREAKING CHANGES
 * Chocolatey Central Management v0.3.0 will only work with Chocolatey Agent v0.11.0+. Upgrade order doesn't matter as you'll need to be on CCM v0.3.0 and Agent v0.11.0 before things start working again. See https://docs.chocolatey.org/en-us/central-management/#ccm-component-compatibility-matrix.

### BUG FIXES
* Fix - Service - Communication with Chocolatey Agent fails on Incorrect Passphrase - see [Licensed #152](https://github.com/chocolatey/chocolatey-licensed-issues/issues/152)
* Fix - Web - Do not recreate website w/bindings on upgrade - see [Licensed #156](https://github.com/chocolatey/chocolatey-licensed-issues/issues/156)


## 0.2.0 (June 18, 2020)
Deployments Release - we are excited to bring about managing remote machines with [Central Management Deployments](https://chocolatey.org/blog/announcing-deployments) coming in this release! There are quite a few things we've brought into the initial release and we think you'll agree that it is a powerful, yet easy to use interface. Read [the announcement.](https://chocolatey.org/blog/announcing-deployments). We've also overhauled the documentation to make it understandable and approachable. Please see https://docs.chocolatey.org/en-us/central-management/.

> :memo: **NOTE**
>
> Log locations have changed. Please see [Central Management FAQs](xref:central-management#faqs) for more information.

### FEATURES
* [Central Management Deployments](https://chocolatey.org/blog/announcing-deployments):
  * Create target groups to deploy to
  * Create a deployment with one or more steps
  * Each step can target multiple groups, and different groups in each step if desired
  * Script a Chocolatey package
  * With additional permissions, run a full PowerShell script instead
  * Choose how failures in each step are handled
  * Reorder steps
  * Control permissions on who can deploy Chocolatey packages and who can run full scripts
  * See progress on active deployments
  * View logs for computers that executed a deployment step
  * Report on completed deployments including exporting to PDF for sharing with executive staff

### BUG FIXES
* [Security] Fix - Framework does not encrypt LDAP Password in the database - see [licensed #144](https://github.com/chocolatey/chocolatey-licensed-issues/issues/144)
* Fix - Service - Error on installation when providing existing certificate: Cannot index into a null array - see [licensed #143](https://github.com/chocolatey/chocolatey-licensed-issues/issues/143)
* Fix - Web - Do not enable recaptcha by default for site registration - see [licensed #128](https://github.com/chocolatey/chocolatey-licensed-issues/issues/128)
* Fix - Web - Create/Edit Computer and Software modals are not saving changes - see [licensed #125](https://github.com/chocolatey/chocolatey-licensed-issues/issues/125)
* Fix - Web - Remove default permission to edit software and computers
* Fix - Web - Restrict What Can Be Created or Edited For Computers and Software
* Fix - Web - Deleted/Hidden items are still being used for counts for paging purposes in Software
* Fix - Web - The license count looks clickable at times when it is not clickable
* Fix - Web - After installation of CCM, doing an iisreset breaks the site
* Fix - All - Monitoring chocolatey.config for changes could potentially lock the file from being written to by choco
* Fix - All - Logging - CCM service not responding to calls and stops logging after choco configuration file is edited
* Fix - Service - Changing CentralManagementServiceUrl value in chocolatey.config causes running management service to crash

### IMPROVEMENTS
* Web - Allow removing computers as a default permission for ccmadmin role - see [licensed #133](https://github.com/chocolatey/chocolatey-licensed-issues/issues/133)
* Service - On install/upgrade, write out the FQDN and link to provide to chocolatey agents
* Logging - Service and DB Migrator should log to the root logs folder of Chocolatey Installation
* All - Logging - Adjust format to match closer with other Chocolatey log file formats
* Service - Set higher encryption when available (TLS 1.2)
* Database Install - Add `/SkipDatabasePermissionCheck` parameter to skip permissions check - see [licensed #147](https://github.com/chocolatey/chocolatey-licensed-issues/issues/147)
* Trial licenses that do not include counts will allow 100 licenses - see [licensed #140](https://github.com/chocolatey/chocolatey-licensed-issues/issues/140)


## 0.1.1 (January 30, 2020)
### BUG FIXES
* [Security] Fix - Database - Don't emit Connection String information to log file
* [Security] Fix - Web - Add missing ability to use Active Directory (LDAP) for authentication
* Fix - Web - Error on installation 'HTTP Error 500.21 - Internal Server Error Handler "aspNetCore" has a bad module "AspNetCoreModule" in its module list' - see [Licensed #114](https://github.com/chocolatey/chocolatey-licensed-issues/issues/114)
* Fix - Service - Unable to parse netsh entries that contain hostname:port bindings - see [Licensed #96](https://github.com/chocolatey/chocolatey-licensed-issues/issues/96)
* Fix - Web - When setting SMTP configuration the SSL checkbox status is being ignored - see [Licensed #87](https://github.com/chocolatey/chocolatey-licensed-issues/issues/87)
* Fix - Service - "The remote server returned an unexpected response: (413) Request Entity Too Large." - see [Licensed #95](https://github.com/chocolatey/chocolatey-licensed-issues/issues/95)
* Fix - Service - Unable to install CCM service with less than PowerShell v5 due to error on New-Guid cmdlet
* Fix - Web - Time discrepancy between Computers and Computer details - see [Licensed #97](https://github.com/chocolatey/chocolatey-licensed-issues/issues/97)
* Fix - Web - Remove ability to brand sections of CCM for now as it wasn't meant to be there yet and doesn't work
* Fix - Service - Unable to uninstall chocolatey-management-service due to incorrect name in package uninstall script
* Fix - Web - License count information is not being displayed correctly (e.g. 90 / n/a) - see [Licensed #80](https://github.com/chocolatey/chocolatey-licensed-issues/issues/80)
* Fix - Service - IP Address of Computer is not updating - see [Licensed #86](https://github.com/chocolatey/chocolatey-licensed-issues/issues/86)
* Fix - Web - Unable to upload a profile picture for user
* Fix - Web - Hovering over tooltips in Internet Explorer causes the page to jump
* Fix - Web - Clicking the Chocolatey icon in top left hand corner opens new tab
* Fix - Web - Website Logs are not appearing the in Maintenance Tab
* Fix - All - Move from DEBUG level reporting by default to INFO level reporting to reduce amount of logging
* Fix - Web - Improve wording in email templates and ensure consistent naming is used

### IMPROVEMENTS
* Database - Check whether provided SQL Server connection string actually works prior to starting installation
* Web - Optimize/Reduce Size of Chocolatey package by removing unnecessary files - see [Licensed #62](https://github.com/chocolatey/chocolatey-licensed-issues/issues/62)
* All - Show a warning when no package parameters are passed when initially installing CCM packages
* All - Show a warning during installation when provided SQL Server connection string doesn't provide an explicit user/password to connect with
* Service - Adjust logs to provide more appropriate information for normal operations
* Web - Autofocus on new password text box on password change screen


## 0.1.0 (May 22, 2019)

Initial preview release

### FEATURES
* Reports - Ability to view and generate report (Excel/PDF) for all currently outdated software
* Dashboard - Provide a dashboard screen with key KPI values
* Overview - Show number of machines checking into CCM and compare to number currently licensed

### BUG FIXES
* Fix - Packaging - Before upgrading Web Package ensure that dotnet process isn't running
* Fix - Web Site - Ensure that minified versions of all assets are used
* Fix - Web Site - Ensure consistent Date/Time Formatting used everywhere
* Fix - Web Site - Corrected duplicate display of search input box on some screens
* Fix - Web Site - Error when attempting to sort by any column in table on Computer Details screen
* Fix - Web Site - Error when attempting to sort by Name or Package Title column in table on Software screen
* Fix - Web Site - Tab does not sort by outdated first on Software screen
* Fix - Web Site - Timezone modification doesn't provide useful information to user
* Fix - Web Site - Only show Software that is installed on at least one machine
* Fix - Web Site - Excel Export generates errors when DateTime values are included
* Fix - Versioning - Ensure correct version number is stamped on all generated assemblies
* Fix - Service - Correct usage of default port number, which should be 24020
* Fix - Service - New-SelfSignedCertificate usage doesn't work on earlier PowerShell versions
* Fix - Service - Ensure correct error handling for incorrect/missing SQL Server credentials
* Fix - Database - Ensure SQL Server 2008 support
* Fix - Database - Migrator doesn't exit with non-zero exit code when there is an error
* Fix - Installation - Ensure usage of FQDN for all components

### IMPROVEMENTS
* Logging - Provided better logging during Service Certificate installation
* Installation - Verify and usage persisted appsettings.json file during upgrade
* Installation - Reduce issues unpacking web package by shortening paths in packaging
* Uninstallation - Remove modifications that were done as part of installation
* Database - Don't attempt to seed database tables every time application starts
* Packaging - Removed unnecessary files from package, making it much smaller
* Packaging - Added required dependencies to packages
* Packaging - Add information about available installation parameters to package description
* Service - Allow modification of configuration settings without the need to restart Windows Service


## 0.1.0-beta-20181009 (October 9, 2018)
### FEATURES
* [Security] Installation - Provide encryption for all persisted configuration data
* [Security] Installation - Sign all PowerShell Scripts and assemblies shipped as part of release
* [Security] Web Site - Provide full RBAC to site and API
* Audit - Provide ability to list all computers that are currently in use across environment
* Audit - Provide ability to list all software that is currently installed across environment
* Reports - Ability to view and generate report (Excel/PDF) for all currently installed software
* Reports - Ability to view and generate report (Excel/PDF) for all computers currently in use
