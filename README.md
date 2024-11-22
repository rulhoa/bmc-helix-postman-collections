# bmc-helix-postman-collections

## What is this project about?

This is a repository of Postman Collections and Environments resources for use with the BMC Helix platform to help with the use of existing APIs for automations calls.

The collection has a script that, whenever you make any API call, it automatically updates the authentication token silently in the background so you don't have to do that manually.

### What's Postman?

It's basically a program you install on your machine and use it to assemble and run REST API calls. Much better than having a bunch of random notes and scripts laying around.

You can download the free version from their website here: https://www.postman.com/

### What's a Postman Collection?

It's basically a collection of folders and API calls that you can export and import into Postman.

The screenshot below is what's contained in the "Generic - Helix API Operations.postman_collection.json" file you can find in this repo:

![Screenshot of the Postman collection](readme_files/collection-2023-05-31.png)


The neat thing about Postman collections is that you can write scripts in them, such as the one included in the collection above that updates the authentication token automatically for you (screenshot below).

![Screenshot of the Postman collection script](readme_files/postman_scripts.png)



### And what are Postman Environments?

In a Collection you can define variables (e.g. username, password, API key, URL, etc) and it's a great way to make your life easier by not needing to change every API call when, for example, your tenant URL changes.

Screenshot of the variables defined in the collection:

![Screenshot of the Postman collection variables](readme_files/collection_variables.png)

Example of one of them being used:

![Screenshot of the Postman variable being used](readme_files/variable_usage.png)


They start becoming limited when you have multiple different tenants that you need to interact with and don't want to have to keep changing variables or creating copies of the Collection for each environment and run the risk of not knowing which is the latest version of your work.

To solve that, Postman has what it calls Environments, which are collection of variables that you can quickly swap between. Using this you can quickly jump back and forth between environments and always use the same Collection of APIs!

Here in the repo we have an Environment definition file ready for you to use with our Collection:
"Helix.postman_environment.json"

Note that when an Environment is enabled, it'll override the value of any variable with the same name defined in the Collection.
In other words:
- Environment not enabled? Postman uses Collection variable values.
- Environment enabled? Postman uses Environment variables and only uses Collection variables not defined in the Environment.

Also note that the automation that updates tokens will ALWAYS try to update the Collection AND the currently enabled Environment corresponding variables. So it'll work no matter which way you prefer to use Postman variables.


## What does this Postman collection contain?

At last count, there were over 220 different REST API calls; many with examples!
Aside from documented endpoints, there are several that BMC support uses as workarounds, many enable actions that officially can only be done via the UI at this moment - aka. subject to change by product teams but works and enables us to do stuff via code!

Below is the summary of what's available:

- 1.0 - Authentication calls (to get auth token)
- 2.0 - BHOM
	- Events (export, create, delete, etc)
	- Policies
	- Data Tables
	- Metrics
	- Notification Service (webhooks)
	- Feature Flag
	- TMF Alarms
- 3.0 - HSM (Service Management / AIOps)
	- Services
	- Blueprints
	- Predictions
	- Service Health
- 4.0 - Discovery / DSM
	- Search
	- Import
	- Create
- 5.0 - ITSM*
- 6.0 - HIA (Intelligent Automation)
	- Connectors
	- Automation Policies
	- Automation Requests
- 10.0 - Developer tools
- 20.0 - HCO (Capacity)


*ITSM mentioned above was merged from another project and has a lot of examples but needs some love to fix variables to get it fully ready for use.
If anyone uses it or has something better, please share!


## How do I use it?

You just download the two files below and import them into Postman

- Generic - Helix API Operations.postman_collection.json
- Helix.postman_environment.json

And then update the Environment variables with the values of your current tenant. Note that the ones with "token" in the name will be dynamically updated by the automation when you run any of the API calls.

That's it!


## Is what you're doing here the best way to collaborate on this?

I don't know but we must start somewhere and I'm completely open to suggestions!


## Who made this possible?

I've been curating this collection since joining BMC in early 2022 and it's been made possible through the help of a lot of people inside and outside BMC.


## DISCLAIMER

Many endpoints are undocumented and thus not oficially supported. This means they may break without warning. Please flag and/or fix as needed as you use the collection! 

