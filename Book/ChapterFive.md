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