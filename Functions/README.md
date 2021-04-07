# Azure Functions

An Azure Function is a simple way for you to run small pieces of code in the cloud, without having to worry about the infrastructure required to host that code. In addition, with the consumption plan option, you only pay for the time when the code runs. Azure automatically scales your function in response to the demand from users.

To create an Azure Function, choose from the range of templates. The following list is an example of some of the templates available to you.

- **HTTPTrigger:** Use this template when you want the code to execute in response to a request sent through the HTTP protocol.

- **TimerTrigger:** Use this template when you want the code to execute according to a schedule.

- **BlobTrigger:** Use this template when you want the code to execute when a new blob is added to an Azure Storage account.

- **CosmosDBTrigger:** Use this template when you want the code to execute in response to new or updated documents in a NoSQL database.

In a WebJob, you can create a custom retry policy for calls to external systems. This kind of policy can't be configured in an Azure Function.