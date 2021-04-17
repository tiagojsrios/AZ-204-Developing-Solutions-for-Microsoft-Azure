# Azure Event Grid

Azure Event Grid is a fully-managed event routing service running on top of Azure Service Fabric. Event Grid distributes events from different sources, such as Azure Blob storage accounts or Azure Media Services, to different handlers, such as Azure Functions or Webhooks. Event Grid was created to make it easier to build event-based and serverless applications on Azure.

Event sources are responsible for sending events to Event Grid. Each event source is related to one or more event types. For example, Azure Storage is the event source for blob created events. IoT Hub is the event source for device created events. Your application is the event source for custom events that you define.

Azure Event Hub has the concept of an event publisher which is often confused with the event source. A publisher to Event Hub is the user or organization that decides to send events to Event Grid. For example, Microsoft publishes events for several Azure services. You can publish events from your own application.

Topics are represented by a public endpoint and are where the event source sends events to. When designing your application, you can decide how many topics to create. Larger solutions will create a custom topic for each category of related events, while smaller solutions might send all events to a single topic. Event subscribers can filter for the event types they want from a specific topic.

An event handler (sometimes referred to as an event "subscriber") is any component (application or resource) that can receive events from Event Grid.

![Event Grid](4-event-grid.png)

| Field | Description |
|------|------|
| topic | The full resource path to the event source. Event Grid provides this value. |
| subject | Publisher-defined path to the event subject. |
| id | The unique identifier for event. |
| eventType | One of the registered event types for this event source. This is a value you can create filters against, e.g. CustomerCreated, BlobDeleted, HttpRequestReceived, etc. |
| eventTime | The time the event was generated based on the provider's UTC time. |
| data | Specific information that is relevant to the type of event. For example, an event about a new file being created in Azure Storage has details about the file, such as the lastTimeModified value. Or, an Event Hubs event has the URL of the Capture file. This field is optional. |
| dataVersion | The schema version of the data object. The publisher defines the schema version. |
| metadataVersion | The schema version of the event metadata. Event Grid defines the schema of the top-level properties. Event Grid provides this value. |
