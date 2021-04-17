# Azure Event Hub

Event Hubs is an intermediary for the publish-subscribe communication pattern. It is optimized for extremely high throughput, a large number of publishers, security, and resiliency.

Event Hubs lets you build a big data pipeline capable of processing millions of events per second with low latency. It can handle data from concurrent sources and route it to a variety of stream-processing infrastructures and analytics services. It enables real-time processing and supports repeated replay of stored raw data.

## Partions

Partitions are buffers into which the communications are saved. Because of the event buffers, events are not completely ephemeral, and an event isn't missed just because a subscriber is busy or even offline. The subscriber can always use the buffer to "catch up." By default, events stay in the buffer for 24 hours before they automatically expire. Every event hub has at least two partitions, and each partition has a separate set of subscribers.

## Capture

Event Hubs can send all your events immediately to Azure Data Lake or Azure Blob storage for inexpensive, permanent persistence.

## Authentication

All publishers are authenticated and issued a token. This means Event Hubs can accept events from external devices and mobile apps, without worrying that fraudulent data from pranksters could ruin our analysis.

For our aircraft engines, we'll set up our architecture so that Event Hubs will authenticate the communications from our engines. We will then have it use capture to save all the data to Data Lake. Later, we can use all that data to retrain and improve our machine learning models. Finally, our event streams will be picked up by Stream Analytics subscribers. Stream Analytics will use our machine learning model to look for patterns in the sensor data that might indicate problems.