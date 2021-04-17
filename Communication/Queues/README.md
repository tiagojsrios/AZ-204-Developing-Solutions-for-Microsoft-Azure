# Azure Queues

1. Azure Queue Storage

Queue storage is a service that uses Azure Storage to store large numbers of messages that can be securely accessed from anywhere in the world using a simple REST-based interface. Queues can contain millions of messages, limited only by the capacity of the storage account that owns it.

2. Azure Service Bus Queue

Service Bus is a message broker system intended for enterprise applications. These apps often utilize multiple communication protocols, have different data contracts, higher security requirements, and can include both cloud and on-premises services. Service Bus is built on top of a dedicated messaging infrastructure designed for exactly these scenarios.

3. Azure Service Bus Topics

Azure Service Bus topics are like queues, but can have multiple subscribers. When a message is sent to a topic instead of a queue, multiple components can be triggered to do their work. Imagine in a music-sharing application, a user is listening to a song. The mobile app might send a message to the "Listened" topic. That topic will have a subscription for "UpdateUserListenHistory", and a different subscription for "UpdateArtistsFanList". Each of those functions is handled by a different component that receives its own copy of the message.

Internally, topics use queues. When you post to a topic, the message is copied and dropped into the queue for each subscription. The queue means that the message copy will stay around to be processed by each subscription branch even if the component processing that subscription is too busy to keep up.

## Benefits of Queues:

1. **Reliability**: The source component can add a message to the queue and destination components can retrieve the message at the front of the queue for processing. Queues increase the reliability of the message exchange because, at times of high demand, messages can wait until a destination component is ready to process them.
2. **Message delivery guarantees**
   1. **At-Least-Once Delivery**: In this approach, each message is guaranteed delivery to at least one of the components that retrieve messages from the queue. Note, however, that in certain circumstances, it is possible that the same message may be delivered more than once. For example, if there are two instances of a web app retrieving messages from a queue, ordinarily each message goes to only one of those instances. However, if one instance takes a long time to process the message, and a time-out expires, the message may be sent to the other instance as well. Your web app code should be designed with this possibility in mind.
   2. **At-Most-Once Delivery**: In this approach, each message is not guaranteed for delivery, and there is a small chance that it may not arrive. However, unlike At-Least-Once delivery, there is no chance that the message will be delivered twice. This is sometimes referred to as *automatic duplicate detection*.
   3. **First-In-First-Out (FIFO)**: If your distributed application requires that messages are processed in precisely the correct order, you must choose a queue system that includes a FIFO guarantee.
3. **Transactional Support**: In the case, we want to make sure all messages get processed, or none of them are processed. We won't be in business long if the credit card message is not delivered, and all our orders are fulfilled without payment! You can avoid these kinds of problems by grouping the two messages into a transaction. Message transactions succeed or fail as a single unit - just like in the database world.