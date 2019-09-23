Liveliness
==============================
The Liveliness QoS can be used to ensure whether particular entities are alive or not.

You can select AUTOMATIC, MANUAL_BY_PARTICIPANT or MANUAL_BY_TOPIC liveliness. If you select AUTOMATIC or 
MANUAL_BY_PARTICIPANT either for publisher or subscriber, you can establish a value for the lease duration and 
announcement period or remain them as infinite. But if the kind selected is MANUAL_BY_TOPIC, you can only establish 
a value for the lease duration as the announcement period is not used for this configuration.

In the AUTOMATIC liveliness kind, the service takes the responsibility for renewing the timer associated to the lease 
duration as long as the DomainParticipant keeps running and remote participants remain connected, considering all the 
entities within the DomainParticipant alive.

The remaining kinds (MANUAL_BY_PARTICIPANT and MANUAL_BY_TOPIC) need periodically an assertion to consider the remote 
participants as alive. That assertion can be done by writing new data or using the function *assert_liveliness*. The 
main difference between these two kinds is that MANUAL_BY_PARTICIPANT requires only the assertion of one of its 
entities to consider that all of them are alive, while MANUAL_BY_TOPIC requires at least one assertion per publisher 
to consider it as alive.

In this test, we are going to create a Publisher using MANUAL_BY_TOPIC and a Subscriber using MANUAL_BY_PARTICIPANT 
and a lease duration value lower than the write rate of the publisher.

**Step-by-Step**

First, you have to launch two instances and create a Publisher and a Subscriber:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Select MANUAL_BY_TOPIC.
   - Set Lease Duration to 50. (The default write rate is 75 ms)

2 - Create a square subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select MANUAL_BY_PARTICIPANT.
   - Set a value for the Lease Duration higher or equal to the one stated for the Publisher. 
     (If the value of subscriber lease duration is lower the entities don't match)

.. image:: test8_1.png
   :scale: 60 %
   :alt: Initial state
   :align: center


As you can see both matches even if they have different liveliness kinds since the standard established that they 
are considered as compatible as long as the offered kind is greater than the required one (considering this order 
AUTOMATIC < MANUAL_BY_PARTICIPANT < MANUAL_BY_TOPIC).

If you go to the *Output Tab* on Instance2, you can observe that the subscriber is continuously losing and recovering 
the liveliness due to the value established for the lease duration, which is lower than the publishing rate. This fact 
makes that the liveliness timer ends up before a new sample comes from the publisher and therefore the subscriber 
shows the liveliness lost message. After that, a new sample arrives at the subscriber side, who notifies about the 
liveliness recover.

.. image:: test8_2.png
   :scale: 60 %
   :alt: State 1
   :align: center
