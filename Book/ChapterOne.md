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