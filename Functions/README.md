# Azure Functions

Azure Functions is a serverless application platform. It allows developers to host business logic that can be executed without provisioning infrastructure. Functions provides intrinsic scalability and you are charged only for the resources used (only pay for the time when the code runs). Azure automatically scales your function in response to the demand from users.

In a WebJob, you can create a custom retry policy for calls to external systems. This kind of policy can't be configured in an Azure Function.

A function app is a way to organize and collectively manage your functions. A function app is comprised of one or more individual functions that are managed together by Azure App Service. All the functions in a function app share the same pricing plan, continuous deployment, and runtime version.

All of the functions in an app share a common set of configuration values, and must all be built for the same language runtime. Each function app is an Azure resource that can be configured and managed independently.

## Stateless logic

Stateless functions are great candidates for serverless compute; function instances are created and destroyed on demand. If state is required, it can be stored in an associated storage service.

## Event driven

Functions are event driven. This means they run only in response to an event (called a "trigger"), such as receiving an HTTP request, or a message being added to a queue. You configure a trigger as part of the function definition. This approach simplifies your code by allowing you to declare where the data comes from (trigger/input binding) and where it goes (output binding).

## Execution time

By default, functions have a timeout of 5 minutes. This timeout is configurable to a maximum of 10 minutes. If your function requires more than 10 minutes to execute, you can host it on a VM. Additionally, if your service is initiated through an HTTP request and you expect that value as an HTTP response, the timeout is further restricted to 2.5 minutes. Finally, there's also an option called Durable Functions that allows you to orchestrate the executions of multiple functions without any timeout.

## Execution frequency

If you expect your function to be executed continuously by multiple clients, it would be prudent to estimate the usage and calculate the cost of using functions accordingly.

While scaling, only one function app instance can be created every 10 seconds, for up to 200 total instances. Keep in mind, each instance can service multiple concurrent executions, so there is no set limit on how much traffic a single instance can handle. Different types of triggers have different scaling requirements, so research your choice of trigger and investigate its limits.

## Bindings

1. **Input binding** - An input binding is a connection to a data source. Our function can read data from these inputs.

2. **Output binding** - An output binding is a connection to a data destination. Our function can write data to these destinations.

There are also triggers, which are special types of input bindings that cause a function to execute. An Azure Event Grid notification can be configured as a trigger. A binding type can be used as an input, an output or both. For example, a function can write to Azure Blob Storage output binding, but a blob storage update could trigger another function.

### Binding Properties

Three properties are required in all bindings. You may have to supply additional properties based on the type of binding and storage you are using.

1. **Name** - Defines the function parameter through which you access the data. In a queue input binding, this is the name of the function parameter that receives the queue message content.

2. **Type** - Identifies the type of binding, i.e., the type of data or service we want to interact with.

3. **Direction** - Indicates the direction data is flowing, i.e., is it an input or output binding?

4. **Connection** (Not required by all bindings) - Provides the name of an app setting key that contains the connection string. Bindings use connection strings stored in app settings to keep secrets out of the function code. This makes your code more configurable and secure.

A binding is configured in your function's configuration file, which is named *function.json* and lives in the same folder as your function code.

```json
{
    "name": "headshotBlobIn",
    "type": "blob",
    "path": "thumbnail-images/{filename}",
    "connection": "HeadshotStorageConnection",
    "direction": "in" // Means this is an input binding
},
{
    "name": "headshotBlobOut",
    "type": "blob",
    "path": "thumbnail-images/{filename}",
    "connection": "HeadshotStorageConnection",
    "direction": "out" // Means this is an output binding
}
```

### Binding Expressions

A binding expression is specialized text in function.json, function parameters, or code that is evaluated when the function is invoked to yield a value.

- App settings
- Trigger file name
- Trigger metadata
- JSON payloads
- New GUID
- Current date and time

Most expressions are identified by wrapping them in curly braces. However, app setting binding expressions are wrapped in percent signs rather than curly braces.

## Monitoring dashboard

The ability to monitor your functions is critical during development and in production. The Azure portal provides a monitoring dashboard if you turn on the Application Insights integration.

|       Type      |                                    Purpose                                   |
|:---------------:|:----------------------------------------------------------------------------:|
| Timer           | Execute a function at a set interval.                                        |
| HTTP            | Execute a function when an HTTP request is received.                         |
| Blob            | Execute a function when a file is uploaded or updated in Azure Blob storage. |
| Queue           | Execute a function when a message is added to an Azure Storage queue.        |
| Azure Cosmos DB | Execute a function when a document changes in a collection.                  |
| Event Hub       | Execute a function when an event hub receives a new event.                   |

## Timer Trigger
A timer trigger is a trigger that executes a function at a consistent interval. To create a timer trigger, you need to supply two pieces of information.

1. A Timestamp parameter name, which is simply an identifier to access the trigger in code.
2. A Schedule, which is a CRON expression that sets the interval for the timer.

## HTTP Trigger

An HTTP trigger is a trigger that executes a function when it receives an HTTP request. HTTP triggers have many capabilities and customizations, including:

- Provide authorized access by supplying keys.
- Restrict which HTTP verbs are supported.
- Return data back to the caller.
- Receive data through query string parameters or through the request body.
- Support URL route templates to modify the function URL.

There are three Authorization levels:

- Function
- Anonymous
- Admin

The Function and Admin levels are "key" based. The difference between the two keys is their scope. Function keys are specific to a function. Host keys apply to all functions inside the function app. If your Authorization level is set to Function, you can use either a function or a host key. If your Authorization level is set to Admin, you must supply a host key.

The Anonymous level means that there's no authentication required.

## Blob Trigger

```
samples-workitems/{name}
```

The first part, samples-workitems, represents the blob container that the trigger monitors. The second part, {name} means that every type of file will cause the trigger to invoke the function. The function is invoked because there's no filter. We could make the trigger invoke the function only when a PNG file is added by using syntax like:

```
samples-workitems/{name}.png
```

The last significant piece of information with this concept is the text name. The name represents a parameter in your Azure function that receives the name of the added file. For example, if we upload a file named resume.txt, my Azure function receives that value as a string through a parameter called name.

## Functions Core Tools

The Core Tools are packaged as a single command-line utility named *func*. The Core Tools feature a variety of functions-related capabilities, but their primary purpose is to:

1. Generate the files and folders you need to develop functions on your local computer;
2. Run your functions locally so you can test and debug them;
3. Publish your functions to Azure.

Some common Core Tools commands that you can run in the command line:
- **func init**: Creates an Azure Function project, therefore it's a collection of one or more Azure Functions developed with the same runtime language. It represents a Function App on Azure.
- **func new**: Creates an Azure Function associated to the project that exists in the directory where the command is being used.
- **func start**: Allows the developer to run the Azure Function locally.
- **func azure functionapp publish <app_name>**: Publishes the Azure Function to Azure Cloud, where *<app_name>* represents the Function App.