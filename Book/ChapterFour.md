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
