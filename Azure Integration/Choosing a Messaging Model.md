# What is a Message?

- Contains the raw data, produced by one component and processed by the next
- Contains the data itself, and not just a reference or an alert to that data
- Sending component expects the destination to process the message content

# What is an Event?

Events are more lightweight than messages, and are most often used for broadcast communications.
Senders are called **publishers** and receivers are known as **subscribers**.

- Lightweight *notification* that indicates that something happened.
- May be sent out to multiple receivers, or to none.
- Often intended to 'fan out' or have a large number of subscribers.
- Publishers has no expectation about the action of receivers.

> [!note] Events can also be called 'Discrete Events'

# Choosing Events v. Messages

Events are more likely to be used for broadcasts, wherein publishers have no expectations on what happens with data. It is ephemeral.
Messages are most often used when the application requires a guarantee that the message will be processed.

> [!tip] Does the sending component expect the communication to be processed by the destination?
> **Yes?** - Use Messages
> **No?** - Use Events

Be sure to analyze the application architecture and all the possible use cases before you choose.

---

# Azure Queue Storage / Azure Service Bus

## Queue Storage

A Service that uses Azure Storage to store large numbers of messages that can be securely accessed from anywhere in the world using REST.
Can contain millions of messages

## Service Bus Queues

A message-broken intended for enterprise applications.
Often utilize multiple communication protocols, have different data contracts and higher security requirements, can include both cloud and on-premises services.

## Service Bus Topics

Are like queues but can have multiple subscribers.
When a message is sent to a queue, multiple components can e triggered to do their work.
Internally, topics still use queues. The message is copied and dropped into the queues for each subscription.

# Benefits of Queues

- Increased reliability
- Message Delivery Guarantees
- Transactional Support

# Topics v. Queues v. Queue Storage

## Service Bus Queue

- Need an At-Most-Once delivery guarantee.
- Need a FIFO guarantee.
- Need to group messages into transactions.
- Want to receive messages without polling the queue.
- Need to provide a role-based access model to the queues.
- Need to handle messages larger than 64 KB but less than 100 MB. The maximum message size supported by the standard tier is 256 KB and the premium tier is 100 MB.
- Queue size won't grow larger than 1 TB. The maximum queue size for the standard tier is 80 GB and for the premium tier, it's 1 TB.
- Want to publish and consume batches of messages.

## Service Bus Topics

- Need all features provided by queues, and additionally a pub-sub pattern where messages can be routed to one of multiple subscriptions.

## Queue Storage

- Need an audit trail of all messages that pass through the queue.
- Expect the queue to exceed 1 TB in size.
- Want to track progress for processing a message inside of the queue.
A simple, temporary storage location for messages sent between components of a distributed application.

> [!tip] Use a queue to organize messages and gracefully handle unpredictable surges in demand.

---
