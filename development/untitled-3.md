# .NET

.NET client SDK for KubeMQ.  

Simple interface to work with the KubeMQ server.

## General SDK description <a id="general-sdk-description"></a>

The SDK implements all communication patterns available through the KubeMQ server:

* Events
* EventStore
* Command
* Query
* Queue

## Installation: <a id="installation"></a>

`install-Package KubeMQ.SDK.csharp -Version 1.0.8` 

### Framework Support <a id="framework-support"></a>

* .NET Framework 4.6.1
* .NET Framework 4.7.1
* .NET Standard 2.0

## Configuration <a id="configuration"></a>

The only required configuration setting is the KubeMQ server address.

Configuration can be set by using one of the following:

* Environment Variable
* `appsettings.json` file
* `app.Config` or `Web.config` file
* Within the code

### Configuration via Environment Variable <a id="configuration-via-environment-variable"></a>

Set `KubeMQServerAddress` to the KubeMQ Server Address

### Configuration via appsettings.json <a id="configuration-via-appsettings-json"></a>

Add the following to your appsettings.json:

```text
{
  "KubeMQ": {
    "serverAddress": "{YourServerAddress}:{YourServerPort}"
  }
}
```

1  
2  
3  
4  
5  


### Configuration via app.Config <a id="configuration-via-app-config"></a>

Simply add the following to your app.config:

```text
<configuration>  
   <configSections>  
    <section name="KubeMQ" type="System.Configuration.NameValueSectionHandler"/>      
  </configSections>  
    
  <KubeMQ>  
    <add key="serverAddress" value="{YourServerAddress}:{YourServerPort}"/>
  </KubeMQ>  
</configuration>
```

1  
2  
3  
4  
5  
6  
7  
8  
9  


## Main Concepts <a id="main-concepts"></a>

* Metadata: The metadata allows us to pass additional information with the event. Can be in any form that can be presented as a string, i.e., struct, JSON, XML and many more.
* Body: The actual content of the event. Can be in any form that is serializable into a byte array, i.e., string, struct, JSON, XML, Collection, binary file and many more.
* ClientID: Displayed in logs, tracing, and KubeMQ dashboard\(When using Events Store, it must be unique\).
* Tags: Set of Key value pair that help categorize the message

### Event/EventStore/Command/Query <a id="event-eventstore-command-query"></a>

* Channel: Represents the endpoint target. One-to-one or one-to-many. Real-Time Multicast.
* Group: Optional parameter when subscribing to a channel. A set of subscribers can define the same group so that only one of the subscribers within the group will receive a specific event. Used mainly for load balancing. Subscribing without the group parameter ensures receiving all the channel messages. \(When using Grouping all the programs that are assigned to the group need to have to same channel name\)
* Event Store: The Event Store represents a persistence store, should be used when need to store data on a volume.

### Queue <a id="queue"></a>

* Queue: Represents a unique FIFO queue name, used in queue pattern.
* Transaction: Represents an Rpc stream for single message transaction.

### Event/EventStore/Command/Query SubscribeRequest Object: <a id="event-eventstore-command-query-subscriberequest-object"></a>

A struct that is used to initialize SubscribeToEvents/SubscribeToRequest, the SubscribeRequest contains the following:

* SubscribeType - Mandatory - Enum that represents the subscription type:
* Events - if there is no need for Persistence.
* EventsStore - If you want to receive Events from persistence. See Main concepts.
* Command - Should be used when a response is not needed.
* Query - Should be used when a response is needed.
* ClientID - Mandatory - See Main concepts
* Channel - Mandatory - See Main concepts
* Group - Optional - See Main concepts
* EventsStoreType - Mandatory - set the type event store to subscribe to Main concepts.

## Queue <a id="queue-2"></a>

KubeMQ supports distributed durable FIFO based queues with the following core features:

* Exactly One Delivery - Only one message guarantee will deliver to the subscriber
* Single and Batch Messages Send and Receive - Single and multiple messages in one call
* RPC and Stream Flow - RPC flow allows an insert and pulls messages in one call. Stream flow allows single message consuming in a transactional way
* Message Policy - Each message can be configured with expiration and delay timers. Also, each message can specify a dead-letter queue for un-processed messages attempts
* Long Polling - Consumers can wait until a message available in the queue to consume
* Peak Messages - Consumers can peek into a queue without removing them from the queue
* Ack All Queue Messages - Any client can mark all the messages in a queue as discarded and will not be available anymore to consume
* Visibility timers - Consumers can pull a message from the queue and set a timer which will cause the message not be visible to other consumers. This timer can be extended as needed.
* Resend Messages - Consumers can send back a message they pulled to a new queue or send a modified message to the same queue for further processing.

### Send Message to a Queue <a id="send-message-to-a-queue"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");



            var resSend = queue.SendQueueMessage(new KubeMQ.SDK.csharp.Queue.Message 

            { 

                Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("some-simple_queue-queue-message"), 

                Metadata = "someMeta" 

            }); 

            if (resSend.IsError) 

            { 

                Console.WriteLine($"Message enqueue error, error:{resSend.Error}"); 

            }            
```

### Send Message to a Queue with Expiration <a id="send-message-to-a-queue-with-expiration"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");



            var resSend = queue.SendQueueMessage(new KubeMQ.SDK.csharp.Queue.Message 

            { 

                Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("some-simple_queue-queue-message"), 

                Metadata = "emptyMeta", 

                Policy = new KubeMQ.Grpc.QueueMessagePolicy 

                { 

                    ExpirationSeconds = 20 

                } 

            }); 

            if (resSend.IsError) 

            { 

                Console.WriteLine($"Message enqueue error, error:{resSend.Error}"); 

            }           
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  


### Send Message to a Queue with Delay <a id="send-message-to-a-queue-with-delay"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");



            var resSend = queue.SendQueueMessage(new KubeMQ.SDK.csharp.Queue.Message 

            { 

                Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("some-simple_queue-queue-message"), 

                Metadata = "emptyMeta", 

                Policy = new KubeMQ.Grpc.QueueMessagePolicy 

                { 

                    DelaySeconds =5 

                } 

            }); 

            if (resSend.IsError) 

            { 

                Console.WriteLine($"Message enqueue error, error:{resSend.Error}"); 

            }          
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  


### Send Message to a Queue with Dead-letter Queue <a id="send-message-to-a-queue-with-dead-letter-queue"></a>

```text
  var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");



            var resSend = queue.SendQueueMessage(new KubeMQ.SDK.csharp.Queue.Message 

            { 

                Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("some-simple_queue-queue-message"), 

                Metadata = "emptyMeta", 

                Policy = new KubeMQ.Grpc.QueueMessagePolicy 

                { 

                    MaxReceiveCount = 3, 

                    MaxReceiveQueue = "DeadLetterQueue" 

                } 

            }); 

            if (resSend.IsError) 

            { 

                Console.WriteLine($"Message enqueue error, error:{resSend.Error}"); 

            } 

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  


### Send Batch Messages <a id="send-batch-messages"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var batch = new List<KubeMQ.SDK.csharp.Queue.Message>(); 

            for (int i = 0; i < 10; i++) 

            { 

                batch.Add(new KubeMQ.SDK.csharp.Queue.Message 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray($"Batch Message {i}"), 

                    Metadata = "emptyMeta", 

                    Policy = new KubeMQ.Grpc.QueueMessagePolicy 

                    { 

                        ExpirationSeconds = 1 

                    } 

                }); 

            } 

            var resBatch = queue.SendQueueMessagesBatch(batch); 

            if (resBatch.HaveErrors) 

            { 

                Console.WriteLine($"Message sent batch has errors"); 

            } 

            foreach (var item in resBatch.Results) 

            {                

                if (item.IsError) 

                { 

                    Console.WriteLine($"Message enqueue error, MessageID:{item.MessageID}, error:{item.Error}"); 

                } 

                else 

                { 

                   

                } 

            } 

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  


### Receive Messages from a Queue <a id="receive-messages-from-a-queue"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            queue.WaitTimeSecondsQueueMessages = 1; 

            var resRec = queue.ReceiveQueueMessages(10); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"Received {resRec.MessagesReceived} Messages:"); 

            foreach (var item in resRec.Messages) 

            { 

                Console.WriteLine($"MessageID: {item.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(item.Body)}"); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  


### Peak Messages from a Queue <a id="peak-messages-from-a-queue"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            queue.WaitTimeSecondsQueueMessages = 1; 

            var resPeak = queue.PeakQueueMessage(10); 

            if (resPeak.IsError) 

            { 

                Console.WriteLine($"Message peek error, error:{resPeak.Error}"); 

                return; 

            } 

            Console.WriteLine($"Peaked {resPeak.MessagesReceived} Messages:"); 

            foreach (var item in resPeak.Messages) 

            { 

                Console.WriteLine($"MessageID: {item.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(item.Body)}"); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  


### Ack All Messages In a Queue <a id="ack-all-messages-in-a-queue"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var resAck = queue.AckAllQueueMessagesResponse(); 

            if (resAck.IsError) 

            { 

                Console.WriteLine($"AckAllQueueMessagesResponse error, error:{resAck.Error}"); 

                return; 

            } 

            Console.WriteLine($"Ack All Messages:{resAck.AffectedMessages} completed"); 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  


### Transactional Queue - Ack <a id="transactional-queue-ack"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var transaction = queue.CreateTransaction(); 

            

            var resRec = transaction.Receive(10, 10); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"MessageID: {resRec.Message.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(resRec.Message.Body)}"); 

            Console.WriteLine("Doing some work....."); 

            Thread.Sleep(1000); 

            Console.WriteLine("Done, ack the message"); 

            var resAck = transaction.AckMessage(resRec.Message.Attributes.Sequence); 

            if (resAck.IsError) 

            { 

                Console.WriteLine($"Ack message error:{resAck.Error}"); 

            } 

            Console.WriteLine("Checking for next message"); 

            resRec = transaction.Receive(10, 1); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            }   

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  


### Transactional Queue - Reject <a id="transactional-queue-reject"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var transaction = queue.CreateTransaction(); 

            

            var resRec = transaction.Receive(10, 10); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"MessageID: {resRec.Message.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(resRec.Message.Body)}"); 

            Console.WriteLine("Reject message"); 

            var resRej = transaction.RejectMessage(resRec.Message.Attributes.Sequence); 

            if (resRej.IsError) 

            { 

                Console.WriteLine($"Message reject error, error:{resRej.Error}"); 

                return; 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  


### Transactional Queue - Extend Visibility <a id="transactional-queue-extend-visibility"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var transaction = queue.CreateTransaction(); 

            

            var resRec = transaction.Receive(5, 10); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"MessageID: {resRec.Message.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(resRec.Message.Body)}"); 

            Console.WriteLine("work for 1 seconds"); 

            Thread.Sleep(1000); 

            Console.WriteLine("Need more time to process, extend visibility for more 3 seconds"); 

            var resExt = transaction.ExtendVisibility(3); 

            if (resExt.IsError) 

            { 

                Console.WriteLine($"Message ExtendVisibility error, error:{resExt.Error}"); 

                return; 

            } 

            Console.WriteLine("Approved. work for 2.5 seconds"); 

            Thread.Sleep(2500); 

            Console.WriteLine("Work done... ack the message"); 

 

            var resAck = transaction.AckMessage(resRec.Message.Attributes.Sequence); 

            if (resAck.IsError) 

            { 

                Console.WriteLine($"Ack message error:{resAck.Error}"); 

            } 

            Console.WriteLine("Ack done"); 

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  


### Transactional Queue - Resend to New Queue <a id="transactional-queue-resend-to-new-queue"></a>

```text
  var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var transaction = queue.CreateTransaction(); 

            

            var resRec = transaction.Receive(5, 10); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"MessageID: {resRec.Message.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(resRec.Message.Body)}"); 

            Console.WriteLine("Resend to new queue"); 

            var resResend = transaction.Resend("new-queue"); 

            if (resResend.IsError) 

            { 

                Console.WriteLine($"Message Resend error, error:{resResend.Error}"); 

                return; 

            } 

            Console.WriteLine("Done"); 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  


### Transactional Queue - Resend Modified Message <a id="transactional-queue-resend-modified-message"></a>

```text
var queue = new KubeMQ.SDK.csharp.Queue.Queue("QueueName", "ClientID", "localhost:50000");

            var transaction = queue.CreateTransaction(); 

            

            var resRec = transaction.Receive(3,5); 

            if (resRec.IsError) 

            { 

                Console.WriteLine($"Message dequeue error, error:{resRec.Error}"); 

                return; 

            } 

            Console.WriteLine($"MessageID: {resRec.Message.MessageID}, Body:{KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(resRec.Message.Body)}"); 

            var modMsg = resRec.Message; 

            modMsg.Queue = "receiverB"; 

            modMsg.Metadata = "new metadata"; 

 

            var resMod = transaction.Modify(modMsg); 

            if (resMod.IsError) 

            { 

                Console.WriteLine($"Message Modify error, error:{resMod.Error}"); 

                return; 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  


## Event <a id="event"></a>

Employing several variations of point to point Event communication style patterns. Allows to connect a sender to one or a group of subscribers

* Subscribe to events
* Send stream
* Send single event

#### The KubeMQ.SDK.csharp.Events.LowLevel.Event object: <a id="the-kubemq-sdk-csharp-events-lowlevel-event-object"></a>

Struct used to send and receive Events using the Event pattern. Contains the following fields \(See Main concepts for more details on each field\):

* Channel
* Metadata
* Body
* EventID - set internally
* Store - Boolean, set if the event should be sent to storage.
* ClientID

### Subscribe <a id="subscribe"></a>

This method allows subscribing to events. Both single and stream of events. Pass a delegate \(callback\) that will handle the incoming event\(s\). The implementation uses await and do not block the continuation of the code execution.

Parameters:

* SubscribeRequest - Mandatory-See SubscribeRequest.
* Handler - Mandatory. Delegate \(callback\) that will handle the incoming events.
* ErrorHandler - Mandatory. Delegate \(callback\) that will handle the incoming exceptions.
* CancellationToken – Non-mandatory CancellationToken to cancel the Subscription.

```text
            var ChannelName = "testing_event_channel"; 

            var ClientID = "hello-world-subscriber"; 

            var KubeMQServerAddress = "localhost:50000"; 

      

            var  subscriber = new KubeMQ.SDK.csharp.Events.Subscriber(KubeMQServerAddress); 

            try 

            { 

                subscriber.SubscribeToEvents(new KubeMQ.SDK.csharp.Subscription.SubscribeRequest 

                { 

                    Channel = ChannelName, 

                    SubscribeType = KubeMQ.SDK.csharp.Subscription.SubscribeType.Events, 

                    ClientID = ClientID 

 

                }, (eventReceive) => 

                { 

            

                    Console.WriteLine($"Event Received: EventID:{eventReceive.EventID} Channel:{eventReceive.Channel} Metadata:{eventReceive.Metadata} Body:{ KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(eventReceive.Body)} "); 

                }, 

                (errorHandler) =>                  

                { 

                    Console.WriteLine(errorHandler.Message); 

                }); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  


### Send single <a id="send-single"></a>

This method allows for sending a single event.

#### KubeMQ.SDK.csharp.Events.LowLevel.Event - Mandatory. The actual Event that will be sent. <a id="kubemq-sdk-csharp-events-lowlevel-event-mandatory-the-actual-event-that-will-be-sent"></a>

Initialize Sender with server address from code \(also can be initialized using config file\):

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 
            var channel = new KubeMQ.SDK.csharp.Events.Channel(new KubeMQ.SDK.csharp.Events.ChannelParameters 

            { 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 
            try 

            { 

                var result = channel.SendEvent(new KubeMQ.SDK.csharp.Events.Event() 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending single event") 

                }); 

                if (!result.Sent) 

                { 

                    Console.WriteLine($"Could not send single message:{result.Error}"); 

                } 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

                           } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  


### Send stream <a id="send-stream"></a>

This method allows for sending a stream of events. Use cases: sending a file in multiple packets; frequent high rate of events.

Initialize Sender with server address from code \(also can be initialized using config file\):

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

            var channel = new KubeMQ.SDK.csharp.Events.Channel(new KubeMQ.SDK.csharp.Events.ChannelParameters 

            { 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

 

            try 

            { 

                _ = channel.StreamEvent(new KubeMQ.SDK.csharp.Events.Event 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending stream event") 

                }); 

 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  


## Event Store <a id="event-store"></a>

Employing persistent point to point Event communication style patterns.

The 'EventsStoreType' object:

To receive events from persistence, the subscriber needs to assign one of seven EventsStoreType and the value for EventsStoreTypeValue.

* EventsStoreTypeUndefined - 0 - Should be set when there is no need for eventsStore.\(when using this type there is no need to set EventsStoreTypeValue\)
* StartNewOnly - 1 - The subscriber will only receive new events \(from the time he subscribed\). \(when using this type there is no need to set EventsStoreTypeValue\)
* StartFromFirst - 2 - The subscriber will receive all events from the start of the queue and all future events as well. \(when using this type there is no need to set EventsStoreTypeValue\)
* StartFromLast - 3 - The subscriber will receive the last event in queue and all future events as well. \(when using this type there is no need to set EventsStoreTypeValue\)
* StartAtSequence - 4 - The subscriber will receive events from the chosen Sequence and all future events as well. \(need to provide with long that of the wanted eventID\)
* StartAtTime - 5 - The subscriber will receive events that were "Stored" from a specified DateTime and all future events as well. \(need to provide with chosen time\)
* StartAtTimeDelta - 6 - The subscriber will receive events that were "Stored" from the difference between DateTime.Now minus the delta was chosen. \(need to provide with a long that represents the time delta to check within milliseconds\)

### Subscribe <a id="subscribe-2"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-subscriber"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

            var subscriber = new KubeMQ.SDK.csharp.Events.Subscriber(KubeMQServerAddress); 

            try 

            { 

                subscriber.SubscribeToEvents(new KubeMQ.SDK.csharp.Subscription.SubscribeRequest 

                { 

                    Channel = ChannelName, 

                    SubscribeType = KubeMQ.SDK.csharp.Subscription.SubscribeType.EventsStore, 

                    ClientID = ClientID, 

                    EventsStoreType = KubeMQ.SDK.csharp.Subscription.EventsStoreType.StartFromFirst, 

                    EventsStoreTypeValue = 0 

 

                }, (eventReceive) => 

                { 

 

                    Console.WriteLine($"Event Received: EventID:{eventReceive.EventID} Channel:{eventReceive.Channel} Metadata:{eventReceive.Metadata} Body:{ KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(eventReceive.Body)} "); 

                }, 

                (errorHandler) => 

                { 

                    Console.WriteLine(errorHandler.Message); 

                }); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  


### Send Single <a id="send-single-2"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

 

            var channel = new KubeMQ.SDK.csharp.Events.Channel(new KubeMQ.SDK.csharp.Events.ChannelParameters 

            { 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress, 

                Store = true 

            }); 

            for (int i = 0; i < 10; i++) 

            { 

                try 

                { 

                    var result = channel.SendEvent(new KubeMQ.SDK.csharp.Events.Event() 

                    { 

                        Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending single event store"), 

                        EventID = $"event-Store-{i}", 

                        Metadata = "some-metadata" 

                    }); 

                    if (!result.Sent) 

                    { 

                        Console.WriteLine($"Could not send single message:{result.Error}"); 

                    } 

                } 

                catch (Exception ex) 

                { 

                    Console.WriteLine(ex.Message); 

                } 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  
62  
63  


### Send Stream <a id="send-stream-2"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

            var channel = new KubeMQ.SDK.csharp.Events.Channel(new KubeMQ.SDK.csharp.Events.ChannelParameters 

            { 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

 

            try 

            { 

                for (int i = 0; i < 10; i++) 

                { 

                    _ = channel.StreamEvent(new KubeMQ.SDK.csharp.Events.Event 

                    { 

                        Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - stream event store") 

                    }); 

                } 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  


## Command <a id="command"></a>

Request\Reply communication pattern.

* Subscribe to requests
* Send request

#### The KubeMQ.SDK.csharp.CommandQuery.LowLevel.Request object: <a id="the-kubemq-sdk-csharp-commandquery-lowlevel-request-object"></a>

Struct used to send the request under the Request\Reply pattern. Contains the following fields \(See Main concepts for more details on some field\):

* RequestID - Optional. Used to match Request to Response. If omitted, it will be set internally.
* RequestType - Mandatory. Used to set if a response is expected or not.
* ClientID - Mandatory. Displayed in logs, tracing, and KubeMQ dashboard.
* Channel - Mandatory. The channel that the Responder subscribed on.
* Metadata - Mandatory.
* ReplyChannel - Read-only, set internally.
* Timeout - Mandatory. Max time for the response to return. Set per request. If exceeded an exception is thrown.

The Response object:

Struct used to send the response under the Request\Reply pattern.

The Response Constructors requires the corresponding 'Request' object.

Contains the following fields \(See Main concepts for more details on some field\):

* ClientID - Mandatory. Represents the sender ID the response was sent from.
* RequestID - Set internally, used to match Request to Response.
* Metadata - Optional.
* Body - Mandatory.
* Timestamp -Set Internally, an indication of the time the response was created.
* Executed - Boolean that represents the task the Responder was performed.
* Error - Mandatory - Represents if an error occurred while processing the request.

### Subscribe to Requests <a id="subscribe-to-requests"></a>

This method allows subscribing to receive requests.

parameters:

SubscribeRequest - Mandatory - See SubscribeRequest.

Handler - Mandatory. Delegate \(callback\) that will handle the incoming requests.

Subscribe:

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-subscriber"; 

            var KubeMQServerAddress = "localhost:50000"; 
            KubeMQ.SDK.csharp.CommandQuery.Responder responder = new KubeMQ.SDK.csharp.CommandQuery.Responder(KubeMQServerAddress); 

            try 

            { 

                responder.SubscribeToRequests(new KubeMQ.SDK.csharp.Subscription.SubscribeRequest() 

                { 

                    Channel = ChannelName, 

                    SubscribeType = KubeMQ.SDK.csharp.Subscription.SubscribeType.Commands, 

                    ClientID = ClientID 

                }, (commandReceive) => { 

                    Console.WriteLine($"Command Received: Id:{commandReceive.RequestID} Channel:{commandReceive.Channel} Metadata:{commandReceive.Metadata} Body:{ KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(commandReceive.Body)} "); 

                    return new KubeMQ.SDK.csharp.CommandQuery.Response(commandReceive) 

                    { 

                        Body = new byte[0], 

                        CacheHit = false, 

                        Error = "None", 

                        ClientID = ClientID, 

                        Executed = true, 

                        Metadata = string.Empty, 

                        Timestamp = DateTime.UtcNow, 

                    }; 

 

                }, (errorHandler) => 

                { 

                    Console.WriteLine(errorHandler.Message); 

                }); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  
62  
63  
64  


### Send Request <a id="send-request"></a>

The KubeMQ SDK comes with two similar methods to send a Request and wait for the Response.

SendRequestAsync returns the Response in a Task

SendRequest returns the Response to the Delegate \(callback\) supplied as a parameter.

#### Send Request Async <a id="send-request-async"></a>

This method allows to send a request to the Responder; it awaits for the Response and returns it in a Task.

parameters:

KubeMQ.SDK.csharp.CommandQuery.LowLevel.Request - Mandatory. The Request object to send.

Initialize Initiator with server address from code \(also can be initialized using config file\):

Method: send request

This method allows to send a request to the Responder and returns the Response to the Delegate \(callback\) supplied as a parameter.

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

            var channel = new KubeMQ.SDK.csharp.CommandQuery.Channel(new KubeMQ.SDK.csharp.CommandQuery.ChannelParameters 

            { 

                RequestsType = KubeMQ.SDK.csharp.CommandQuery.RequestType.Query, 

                Timeout = 1000, 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

            try 

            { 

 

                var result = channel.SendRequest(new KubeMQ.SDK.csharp.CommandQuery.Request 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending a command, please reply") 

                }); 

 

                if (!result.Executed) 

                { 

                    Console.WriteLine($"Response error:{result.Error}"); 

                    return; 

                } 

                Console.WriteLine($"Response Received:{result.RequestID} ExecutedAt:{result.Timestamp}"); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  


#### Send Request Async <a id="send-request-async-2"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

            var channel = new KubeMQ.SDK.csharp.CommandQuery.Channel(new KubeMQ.SDK.csharp.CommandQuery.ChannelParameters 

            { 

                RequestsType = KubeMQ.SDK.csharp.CommandQuery.RequestType.Query, 

                Timeout = 1000, 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

            try 

            { 

 

                var result = await channel.SendRequestAsync(new KubeMQ.SDK.csharp.CommandQuery.Request 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending a command, please reply") 

                }); 

 

                if (!result.Executed) 

                { 

                    Console.WriteLine($"Response error:{result.Error}"); 

                    return; 

                } 

                Console.WriteLine($"Response Received:{result.RequestID} ExecutedAt:{result.Timestamp}"); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  


## Query <a id="query"></a>

Request\Reply communication pattern similar to Command. Allows caching the response at the KubeMQ

### Cache mechanism <a id="cache-mechanism"></a>

KubeMQ server allows storing each response in a dedicated cache system. Each request can specify whether or not to use the cache. In case the cache is used, the KubeMQ server will try to return the response directly from the cache and reduce latency.

To use the cache mechanism, add the following parameters to each Request:

CacheKey - Unique key to store the response in the KubeMQ cache mechanism.

CacheTTL - Cache data Time to live in milliseconds per CacheKey.

In the Response object you will receive an indication whether it was returned from cache:

CacheHit - Indication if the response was returned from KubeMQ cache.

### Subscribe to Requests <a id="subscribe-to-requests-2"></a>

```text
Example:

  var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-subscriber"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

 

            KubeMQ.SDK.csharp.CommandQuery.Responder responder = new KubeMQ.SDK.csharp.CommandQuery.Responder(KubeMQServerAddress); 

            try 

            { 

                responder.SubscribeToRequests(new KubeMQ.SDK.csharp.Subscription.SubscribeRequest() 

                { 

                    Channel = ChannelName, 

                    SubscribeType = KubeMQ.SDK.csharp.Subscription.SubscribeType.Queries, 

                    ClientID = ClientID 

                }, (queryReceive) => { 

                    Console.WriteLine($"Command Received: Id:{queryReceive.RequestID} Channel:{queryReceive.Channel} Metadata:{queryReceive.Metadata} Body:{ KubeMQ.SDK.csharp.Tools.Converter.FromByteArray(queryReceive.Body)} "); 

                    return new KubeMQ.SDK.csharp.CommandQuery.Response(queryReceive) 

                    { 

                        Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("got your query, you are good to go"), 

                        CacheHit = false, 

                        Error = "None", 

                        ClientID = ClientID, 

                        Executed = true, 

                        Metadata = "this is a response", 

                        Timestamp = DateTime.UtcNow 

                    }; 

 

                }, (errorHandler) => 

                { 

                    Console.WriteLine(errorHandler.Message); 

                }); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  
62  
63  
64  
65  
66  
67  
68  
69  
70  
71  


### Send request <a id="send-request-2"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

            var channel = new KubeMQ.SDK.csharp.CommandQuery.Channel(new KubeMQ.SDK.csharp.CommandQuery.ChannelParameters 

            { 

                RequestsType = KubeMQ.SDK.csharp.CommandQuery.RequestType.Query, 

                Timeout = 1000, 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

            try 

            { 

 

                var result = channel.SendRequest(new KubeMQ.SDK.csharp.CommandQuery.Request 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending a query, please reply") 

                }); 

 

                if (!result.Executed) 

                { 

                    Console.WriteLine($"Response error:{result.Error}"); 

                    return; 

                } 

                Console.WriteLine($"Response Received:{result.RequestID} ExecutedAt:{result.Timestamp}"); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 
```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  


#### Send request async <a id="send-request-async-3"></a>

```text
var ChannelName = "testing_event_channel";

            var ClientID = "hello-world-sender"; 

            var KubeMQServerAddress = "localhost:50000"; 

 

            var channel = new KubeMQ.SDK.csharp.CommandQuery.Channel(new KubeMQ.SDK.csharp.CommandQuery.ChannelParameters 

            { 

                RequestsType = KubeMQ.SDK.csharp.CommandQuery.RequestType.Query, 

                Timeout = 1000, 

                ChannelName = ChannelName, 

                ClientID = ClientID, 

                KubeMQAddress = KubeMQServerAddress 

            }); 

            try 

            { 

 

                var result = await channel.SendRequestAsync(new KubeMQ.SDK.csharp.CommandQuery.Request 

                { 

                    Body = KubeMQ.SDK.csharp.Tools.Converter.ToByteArray("hello kubemq - sending a query, please reply") 

                }); 

 

                if (!result.Executed) 

                { 

                    Console.WriteLine($"Response error:{result.Error}"); 

                    return; 

                } 

                Console.WriteLine($"Response Received:{result.RequestID} ExecutedAt:{result.Timestamp}"); 

            } 

            catch (Exception ex) 

            { 

                Console.WriteLine(ex.Message); 

            } 

```

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  
47  
48  
49  
50  
51  
52  
53  
54  
55  
56  
57  
58  
59  
60  
61  
62  


