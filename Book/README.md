# Chapter 1. Develop Azure Infrastructure as a Service Compute Solution

- Creating a VM is a straightforward process, but you still need to plan the deployment. You need to consider whether you need to make the application highly available hosted in the virtual machine, or if you need to scale-up and down the number of VMs associated to a load balancer. In such cases, you need to remember to create the availability set before you create the VMs.

- You need to carefully consider when to configure a VM for remote access from the internet. In general, you should not configure remote access over public IPs on production VMs. For those cases, you should deploy a virtual private network and connect to your VM using its private IP.

- Some resources can contain other resources as child elements. This parent-child relationship is not the same as a dependency relationship. The parent-child relationship does not guarantee that the parent will be deployed before its children. You need to use the dependsOn element to ensure the correct deployment order.

- ARM templates are powerful tools that enable you to create custom functions for automating some repeating actions. When you create your custom function, remember the limitations when calling predefined or other custom functions. You should also bear in mind the visibility of the template variables and parameters when working with custom functions.

- The modifications that you make to a container while it’s running do not persist if you reboot the container. If you need to make changes to the content of a container, you need to modify the image container and then redeploy the container. If you need your container to save information that needs to be persisted across reboots, you need to use volumes.

- A container registry is useful not only for storing your container images but also for automating the deployment of containers into the Azure Container services. Any continuous delivery service, like Azure Pipelines, would need a container registry for deploying the container images.

- You can use several authentication mechanisms, such as an individual login with Azure AD, an admin account, or a service principal. Authentication with Azure AD is a good approach for your development and testing environment. Using the admin account is disabled by default and is discouraged for production environments because you need to put the admin account password in your code. For production environments, the recommended way to pull images is using service principals for authentication with the ACR.

- Because Azure App Service does not support the same features for Linux and Windows, you cannot mix Windows and Linux apps in the same resource group in the same region. For more information about the limitations of Linux App Services, review the following article: https://docs.microsoft.com/en-us/azure/app-service/containers/app-service-linux-intro

- When you are planning to configure the application logging, you should consider that not all the programming languages’ codes can write the log information in Blob Storage. You can use Blob Storage only with .NET application logs. If you use Java, PHP, Node.js, or Python, you need to use the application log file system option.

- You can use different mechanisms for deploying your code into an Azure App Service. If you decide to use continuous deployment systems for deploying your code, like Azure Repos, or GitHub, remember that you need to authorize your continuous deployment system before you can perform any deployment.

- Remember that the settings that you configure in the Application Settings section overwrite the values that you configure in the <appSettings> or <connectionStrings> in your Web.config or appsettings.json files.

- Autoscaling allows you to assign resources to your application in an efficient way. Autoscale rules for adding more instances to your application do not remove those instances when the rule condition is not satisfied. As a best practice, if you create a scale-out rule for adding instances to a service, you should create the opposite scale-in rule for removing the instance. This ensures that the resources are assigned efficiently to your application.

- Remember that you need to install the extensions on your local environment before you can use bindings or triggers. You can use the func command-line command from the Azure Function CLI tools.

- When you work with Azure Functions, you can choose between versions 1.0, 2.0, and 3.0. The main difference between the versions 1.0 and the other versions is that you can only develop and host Azure Functions 1.0 on Azure portal or Windows computers. Functions 2.0 and 3.0 can be developed and hosted on all platforms supported by .NET Core. The Azure Function you use affects the extension packages that you need to install when configuring triggers and bindings.

- In earlier versions of Azure Functions, the authentication information was available only to ASP.NET projects using the ClaimsPrincipal class. Now you can access that information by reading the special HTTP Headers set by the App Service. For a complete list of authentication headers refer to the article https://docs.microsoft.com/en-us/azure/app-service/app-service-authentication-how-to#access-user-claims

- When working with Azure Durable Functions, remember that you can pass information between the different functions in the workflow by using the binding mechanism.

## Chapter Summary:

1. Azure provides computing services for deploying your own virtualized infrastructure directly in the cloud. You can also deploy hybrid architectures to connect your on-premises infrastructure with your IaaS resources.
2. Azure Resource Manager is the service in Azure that manages the different resources that you can deploy in the cloud. You can define the resources and their dependencies by using a JSON-based file called an ARM template.
3. A container image is a package of software in which you store your code and any library or dependencies for running your application in a highly portable environment.
4. When you create a new instance of a container image, each of these instances is named a “container.”
5. You can store your container images in a centralized store called a registry.
6. Azure Container Registry is a managed registry, which is based on the open-source specification of Docker Registry 2.0.
7. You can run your containers in several Azure services, such as Azure Managed Kubernetes Service, Azure Container Instance, Azure Batch, Azure App Service, or Azure Container Service.
8. Azure provides you with needed services for deploying serverless solutions, allowing you to center on the code and forget about the infrastructure.
9. Azure App Services is the base of the serverless offering. On top of App Services, you can deploy web apps, mobile back-end apps, REST APIs, or Azure Functions and Azure Durable Functions.
10. When you work with App Services, you are charged only by the time that your code is running.
11. App Services runs on top of App Services Plans.
12. An App Service Plan provides the resources and virtual machines needed for running your App Services code.
13. You can run more than one App Service on top of a single App Service Plan.
14. When troubleshooting your App Service application, you can use several types for diagnostics logging: webserver logging and diagnostics, detailed error, failed requests, application diagnostics, and deployment diagnostics.
15. Diagnostics logging is stored locally on the VM, where the instance of your application is running.
16. Horizontal scaling or in-out scaling is the process of adding or removing instances of an application.
17. Vertical scaling or up-down scaling is the process of adding or removing resources to the same virtual machine that hosts your application.
18. Scale In/Out doesn’t have an effect on the availability of the application.
19. Vertical scaling affects the availability of the application because the application needs to be deployed in a virtual machine with the new resources assignment.
20. You can add and remove resources to your applications by using autoscale rules.
21. You can apply autoscale only to some Azure Resource types.
22. Autoscale depends on Azure virtual machine scale sets.
23. Your application needs to be aware of the changes in the resources assignment.
24. Azure Functions is the evolution of WebJobs.
25. Azure Functions use triggers and bindings for creating instances of Azure functions and sending or receiving data to or from external services, like Queue storage or Event Hub.
26. There are three versions of Azure Functions. Version 1.0 only supports .NET Framework and Windows environments. Version 2.0 and later support .NET Core and Windows and Linux environments.
27. When you work with triggers and bindings, you need to install the appropriate NuGet package for function extension that contains that trigger or binding.
28. Azure Function runtime already includes extensions for Timers and HTTP triggers. You don’t need to install specific packages for using these trigger bindings.
29. Triggers that create function instances can be based on data operations, timers, or webhooks.
30. Azure Durable Functions is the evolution of Azure Functions that allow you to create workflows where the state of the instances is preserved in case of VM restart or function host process respawn.
31. Orchestration functions define the activity and the order of execution of the functions that do the job.
32. Activity functions contain the code that makes the action that you need for a step in the workflow, like sending an email, saving a document, or inserting information in a database.
33. Client functions create the instance of the orchestration function using an orchestration client.
34. Azure Function Apps provides the resources needed for running Azure Functions and Durable Functions.

# Chapter 2. Develop for Azure Storage

- You can use different APIs for accessing your Cosmos DB database. Each API offers different feature depending on the way you need to represent your data. Remember that you cannot change the API once you have created your Cosmos DB database.

- Remember that your data is distributed across the different logic partitions by using the partition key. For this reason, once you have chosen a partition key, you cannot change it.

- The consistency level impacts the latency and availability of the data. In general terms, you should avoid the most extreme levels as they have a more significant impact on your program that should be carefully evaluated. If you are unsure of which level of consistency should use, you should use the session level, as this is the best-balanced level.

- You need to plan carefully how to create a new container in Azure Cosmos DB. You can set some of the properties that you can configure only during the creation process. Once you have created the container if you need to modify those properties, you need to create a new container with the needed values and migrate the data to the new container.

- When you are performing copy or move operations on containers or blobs, you are not limited to the same storage account. You can copy blobs and containers between Storage Accounts in different regions or even subscriptions, as long as you have enough privileges for accessing to both accounts.

- When you need to move a blob to any destination, container, or Storage Account, remember that you need first to perform a copy operation and then delete the source blob. There is no such move method in the CloudBlockBlob class.

- Leasing is the mechanism that you need to use to ensure that no other users or processes can access a blob while you are working with it. You can create timed or infinite leases. Remember that you need to release infinite leases manually.

- You should not try to change the access tier for a blob that is stored in an Azure Storage Account Gen1. Only Azure Storage Account Gen2 allows working with access tiers. If you try to use the SetAccessTier() method with a blob in an Azure Storage Account Gen1, you get an exception.

- You can move from hot to cool and vice versa to access tiers without needing to wait for rehydration. The rehydration process only happens when you move a blob from the archive to any other access tier.

1. Cosmos DB is a premium storage service that provides low-latency access to data distributed across the globe.
2. The PartitionKey system property defines the partition where the entity is stored. 
3. Choosing the correct PartitionKey is critical for achieving the right performance level. 
4. You can access Cosmos DB using different APIs: SQL, Table, Gremlin (Graph), MongoDB, and Cassandra. 
5. You can create your custom indexes in Cosmos DB.
6. You can choose the property that is used as the partition key. 
7. You should avoid selecting partition keys that create too many or too few logical partitions. 
8. A logical partition has a limit of 20 GB of storage. 
9. Consistency levels define how the data is replicated between the different regions in a Cosmos DB account. 
10. There are five consistency levels: strong, bounded staleness, session, consistent prefix, and eventual. 
11. Strong consistency level provides a higher level of consistency but also has a higher latency. 
12. Eventual consistency level provides lower latency and lower data consistency. 
13. You can move blob items between containers in the same Storage Account or containers in different Storage Accounts. 
14. Azure Blob Storage service offers three different access tiers with different prices for storage and accessing data.
15. You can automatically manage the movement between access tiers by implementing lifecycle management policies.

# Chapter 3. Implement Azure security

- When you are working with OAuth2 authentication, remember that you don’t need to store the username and password information in your system. You can delegate that task in specialized authentication servers. Once the user has been authenticated successfully, the authentication server sends an access token that you can use for confirming the identity of the client. This access token needs to be refreshed once the token expires. The OAuth2 can use a refresh token for requesting a new access token without asking the user again for his or her credentials.

- If you plan to work with user delegation SAS, you need to consider that this type of SAS is available only for Azure Blob Storage and Azure Data Lake Storage Gen2. You cannot use either Stored Access Policies when working with user delegation SAS.

- When you are registering a new application in your Azure Active Directory tenant, you need to consider which will be your target user. If you need for any user from any Azure Active Directory organization to be able to log into your application, you need to configure a multitenant app. In those multitenant scenarios, the app registration and management is always performed in your tenant and not in any other external tenant.

- When you are assigning specific service roles, carefully review the permissions granted by the role. In general, granting access to a resource doesn’t grant access to the data managed by that resource. For example, the Storage Account Contributor grants access for managing Storage Accounts but doesn’t grant access to the data itself.

- When you are defining your key-value pair, remember that you are limited to a maximum length of 10,000. Remember also that keys are case-sensitive, so “AppSetting” and “appsetting” are treated as different keys.

- The kind of information that you usually store in an Azure Key Vault is essential information that needs to keep secret, like passwords, connection strings, private keys, and things like that. When configuring the access to your Key Vault, carefully review the access level you grant to the security principal. As a best practice, you should always apply the principle of least privilege. You grant access to the different levels in a Key Vault by creating Access Policies.

- You can configure two different types of managed identities: system- and user-assigned. System-assigned managed identities are tied to the service instance. If you delete the service instance, the system-assigned managed identity is automatically deleted as well. You can assign the same user-assigned managed identities to several service instances.

1. Authentication is the act of proving that a user is who he or she claims to be. 
2. A user authenticates by providing some information that the user only knows. 
3. There are several mechanisms of authentication that provide different levels of security.
4. Some of the authentication mechanisms are form-based, token-based, or certificate-based. 
5. Using form-based authentication requires your application to store your users’ passwords. 
6. Form-based authentication requires HTTPS to make the authentication process more secure. 
7. Using token-based authentication, you can delegate the authorization to third-party authentication providers. 
8. You can add social logins to your application by using token-based authentication.
9. Multifactor authentication is an authentication mechanism that requires the users to provide more than one piece of information that only the user knows. 
10. You can easily implement multifactor authentication by using Azure Active Directory. 
11. There are four main actors in OAuth authentication: client, resource server, resource owner, and authentication server. 
12. The resource owner needs to authenticate the client before sending the authorization grant. 
13. The access token grants access to the resource hosted on the resource server. 
14. The authorization grant or authorization code grants the client the needed rights to request an access token to the authorization server.
15. The client uses the refresh token to get a new access token when it expires without needing to request a new authorization code. 
16. The JSON web token is the most extended implementation of OAuth tokens. 
17. Shared Access Signatures (SAS) is an authentication mechanism for granting access to Azure Storage Accounts without sharing account keys. 
18. Shared Access Signatures (SAS) tokens must be signed. 
19. There are three types of SAS token: user delegation, account, and service SAS. 
20. User delegation SAS tokens are signed using a key assigned to an Azure Active Directory user. 
21. Account and Service SAS are signed using the Azure Storage account key. 
22. You can hide the details of the SAS tokens from the URL by using Stored Access Policies.
23. Shared access signature tokens provide fine-grained access control to your Azure storage accounts. 
24. You can create an SAS token for service, container, and item levels. 
25. You need to register applications in Azure Active Directory for being able to authenticate users using your tenant. 
26. There are three account types supported for authentication: accounts only in the organizational directory, accounts in any organizational directory, and Microsoft accounts. 
27. You need to provide a return URL for authenticating your application when requesting user authentication. 
28. You need to configure a secret or a certificate when your application needs to access information in other APIs. 
29. Role-Based Access Control (RBAC) authorization provides fine-grained access control to the resources. 
30. A security principal is an entity to which you can grant privileges.
31. Security principals are users, groups, service principals, and managed identities. 
32. A permission is an action that a security principal can make with a resource. 
33. A role definition, or role, is a group of permissions. 
34. A scope is a level where you can assign a role. 
35. A role association is a relationship between a security principal, a role, and a scope. 
36. There are four scopes: management groups, subscription, resource group, and resources. 
37. You can centralize the configuration of your distributed application using Azure App Configuration. 
38. Azure App Configuration stores the information using key-value pairs. 
39. Values in the Azure App Configuration are encrypted. 
40. Azure Key Vault provides better security than the Azure App Configuration service. 
41. The limit of size for an Azure App Configuration is 10.000, including the key, label, and value.
42. You can create references from Azure App Configuration items to Azure Key Vault items. 
43. Azure Key Vault allows you to store three types of objects: keys, secrets, and certificates. 
44. You should use managed identities authentication for accessing the Azure Key Vault. 
45. You need to define a certificate policy before creating a certificate in the Azure Key Vault. 
46. If you import a certificate into the Azure Key Vault, a default certificate policy is automatically created for you.

# Chapter 4. Monitor, troubleshoot, and optimize Azure solutions

- Content Delivery Networks (CDN) are appropriate for caching static content that changes infrequently. Although Azure CDN from Akamai and Azure CDN from Verizon include Dynamic Site Acceleration (DSA), this feature is not the same as a cache system. You should not confuse Azure CDN DSA optimization wiht Azure CDN cache.

- You can use Azure Cache for Redis for static content and the most-accessed dynamic data. You can use it for in-memory databases or message queues using a publication/subscription pattern.

- Remember that Application Insights is a solution for monitoring the behavior of an application on different platforms, written in different languages. You can use Application Insights with web applications and native applications or mobile applications written in .NET, Java, JavaScript, or Node.js. There is no requirement to run your application in Azure. You only need to use Azure for deploying the Application Insights resource that you use for analyzing the information sent by your application.

- When you try to query logs from the Azure Monitor, remember that you need to enable the diagnostics logs for the Azure App Services. If you get the message, We didn’t find any logs when you try to query the logs for your Azure App Service, that could mean that you need to configure the diagnostic settings in your App Service.

- Remember that you need a Visual Studio Enterprise license for creating multistep web tests. You use the Visual Studio Enterprise for the definition of the steps that are part of the test, and then you upload the test definition to Azure Application Insights.

- Remember to test your retry strategy carefully. Using a wrong retry strategy could lead your application to exhaust the resources needed for executing your code. A wrong retry strategy can potentially lead to infinite loops if you don’t use circuit breakers.

1. Your application needs to be able to manage transient faults.
2. You need to determine the type of fault before retrying the operation. 
3. You should not use immediate retry more than once. 
4. You should use random starting values for the retry periods. 
5. You should use the built-in SDK mechanism when available. 
6. You should test your retry count and interval strategy. 
7. You should log transient and nontransient faults. 
8. You can improve the performance of your application by adding a cache to your application. 
9. Azure Cache for Redis allows the caching of dynamic content. 
10. Using Azure Cache for Redis, you can create in-memory databases to cache the most-used values. 
11. Azure Cache for Redis allows you to use messaging queue patterns. 
12. Content Delivery Networks (CDNs) store and distribute static content in servers distributed across the globe. 
13. CDNs reduce the latency by serving the content from the server nearest to the user.
14. You can invalidate the content of the cache by setting a low TTL (Time-To-Live). 
15. You can invalidate the content of the cache by removing all or part of the content from the cache. 
16. Application Insights gets information from your application and sends it to Azure. 
17. You can use Application Insights with different platforms and languages. 
18. Application Insights is part of the Azure Monitor service.
19. Application Insights generates two types of information: metrics and logs. 
20. Application Insights allows you to create web tests to monitor the availability of your application. 
21. You can configure alerts and trigger different actions associated with web tests.

# Chapter 5. Connect to and consume Azure services and third-party services

- When you are working with Integration Service Environments (ISE), you have specific connectors that run inside the ISE. These special ISE connectors are marked with a label. Although ISE 249environments use dedicated resources for your environment, you still can use global, public, multitenant connectors, like Office 365 or Dropbox connectors.

- You can create custom connectors for Azure Logic Apps, Microsoft Flow, and Microsoft PowerApps. You cannot reuse a connector created for Azure Logic Apps in Microsoft Flow or PowerApps (or vice versa). You can use the same OpenAPI definition to create a custom connector for these three services.

- Event Grid is one of the services that Azure provides for exchanging information between different systems. These systems publish and consume events from the Event Grid, allowing you to decouple the different elements of your architecture. Ensure that you fully understand the role each element plays in the exchange of information using Event Grid.

- The Azure Event Hub is a service appropriate for processing huge amounts of events with low latency. You should consider the event hub as the starting point in an event processing pipeline. You can use the event hub as the event source of the Event Grid service.

1. Azure App Service Logic Apps allows you to interconnect different services without needing to create specific code for the interconnection.
2. Logic App Workflows define the steps needed to exchange information between applications. 
3. Microsoft provides connectors for getting and sending information to and from different services. 
4. Triggers are events fired on the source systems. 
5. Actions are each of the steps performed in a workflow. 
6. Azure Logic Apps provides a graphical editor that eases the process of creating workflows. 
7. You can create your custom connectors for connecting your application with Azure Logic Apps. 
8. A Custom Connector is a wrapper for a REST or SOAP API. 
9. You can create custom connectors for Azure Logic Apps, Microsoft Flow, and Microsoft PowerApps. 
10. You cannot reuse custom connectors created for Microsoft Flow or Microsoft PowerApps with Azure Logic Apps.
11. You can export your Logic Apps as Azure Resource Manager templates. 
12. You can edit and modify the Logic Apps templates in Visual Studio. 
13. The API Management service allows you to publish your back-end REST or SOAP APIs using a common and secure front end. 
14. You need to create subscriptions in the APIM service for authenticating the access to the API. 
15. You need to create a product for publishing a back-end API. 
16. You can publish only some operations of your back-end APIs. 
17. APIM Policies allow you to modify the behavior of the APIM gateway. 
18. An event is a change in the state of an entity. 
19. In an event-driven architecture, the publisher doesn’t have the expectation that the event is processed or stored by a subscriber. 
20. Azure Event Grid is a service for implementing event-driven architectures. 
21. An Event Grid Topic is an endpoint where a publisher service can send events. 
22. Subscribers are services that read events from an Event Grid Topic. 
23. You can configure several types of services as event sources or event subscribers in Azure Event Grid.
24. You can create custom events for sending them to the Event Grid. 
25. You can subscribe to your custom application with an Event Grid Topic by using WebHooks. 
26. The Azure Notification Hub is a service that unifies the push notifications on mobile platforms. 
27. You can connect the push notification services from the different manufacturers to the Azure Notification Hub. 
28. The Azure Event Hub is the entry point for Big Data event pipelines. 
29. Azure Event Hub is specialized in ingesting millions of events per second with low latency. 
30. You can use Azure Event Hub as an event source for the Event Grid service. 
31. You can use AMQP, Kafka, and HTTPS for connecting to Azure Event Hub. 
32. In a message-driven architecture, the publisher application has the expectation that the message is processed or stored by the subscriber.
33. The subscriber needs to change the state once the message is processed. 
34. A message is raw data sent by a publisher that needs to be processed by a subscriber. 
35. Azure Service Bus and Azure Queue message are message broker services.