# Azure Functions

Azure Functions is a serverless application platform. It allows developers to host business logic that can be executed without provisioning infrastructure. Functions provides intrinsic scalability and you are charged only for the resources used (only pay for the time when the code runs). Azure automatically scales your function in response to the demand from users.

To create an Azure Function, choose from the range of templates. The following list is an example of some of the templates available to you.

- **HTTPTrigger:** Use this template when you want the code to execute in response to a request sent through the HTTP protocol.

- **TimerTrigger:** Use this template when you want the code to execute according to a schedule.

- **BlobTrigger:** Use this template when you want the code to execute when a new blob is added to an Azure Storage account.

- **CosmosDBTrigger:** Use this template when you want the code to execute in response to new or updated documents in a NoSQL database.

In a WebJob, you can create a custom retry policy for calls to external systems. This kind of policy can't be configured in an Azure Function.

A function app is a way to organize and collectively manage your functions. A function app is comprised of one or more individual functions that are managed together by Azure App Service. All the functions in a function app share the same pricing plan, continuous deployment, and runtime version.

## Stateless logic

Stateless functions are great candidates for serverless compute; function instances are created and destroyed on demand. If state is required, it can be stored in an associated storage service.

## Event driven

Functions are event driven. This means they run only in response to an event (called a "trigger"), such as receiving an HTTP request, or a message being added to a queue. You configure a trigger as part of the function definition. This approach simplifies your code by allowing you to declare where the data comes from (trigger/input binding) and where it goes (output binding).

| Service | Trigger description |

Blob storage	Starts a function when a new or updated blob is detected.
Azure Cosmos DB	Start a function when inserts and updates are detected.
Event Grid	Starts a function when an event is received from Event Grid.
HTTP	Starts a function with an HTTP request.
Microsoft Graph Events	Starts a function in response to an incoming webhook from the Microsoft Graph. Each instance of this trigger can react to one Microsoft Graph resource type.
Queue storage	Starts a function when a new item is received on a queue. The queue message is provided as input to the function.
Service Bus	Starts a function in response to messages from a Service Bus queue.
Timer	Starts a function on a schedule.

## Execution time

By default, functions have a timeout of 5 minutes. This timeout is configurable to a maximum of 10 minutes. If your function requires more than 10 minutes to execute, you can host it on a VM. Additionally, if your service is initiated through an HTTP request and you expect that value as an HTTP response, the timeout is further restricted to 2.5 minutes. Finally, there's also an option called Durable Functions that allows you to orchestrate the executions of multiple functions without any timeout.

## Execution frequency

If you expect your function to be executed continuously by multiple clients, it would be prudent to estimate the usage and calculate the cost of using functions accordingly.

While scaling, only one function app instance can be created every 10 seconds, for up to 200 total instances. Keep in mind, each instance can service multiple concurrent executions, so there is no set limit on how much traffic a single instance can handle. Different types of triggers have different scaling requirements, so research your choice of trigger and investigate its limits.

## Bindings

Bindings know how to talk to different services, which means you don't have to write code in your function to connect to data sources and manage connections. Each binding has a direction - your code reads data from input bindings, and writes data to output bindings. Each function can have zero or more bindings to manage the input and output data processed by the function.

## Monitoring dashboard

The ability to monitor your functions is critical during development and in production. The Azure portal provides a monitoring dashboard if you turn on the Application Insights integration.