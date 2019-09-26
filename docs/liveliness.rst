Liveliness
==============================
The Liveliness QoS can be used to ensure whether particular entities are alive or not. There are three different kinds
of liveliness: AUTOMATIC, MANUAL_BY_PARTICIPANT or MANUAL_BY_TOPIC liveliness. When any of the first two is selected,
a value for the lease duration and announcement period can be set. If MANUAL_BY_TOPIC is selected, only the lease
duration can be configured, as the announcement period is not used for this mode.

In the AUTOMATIC liveliness kind, the service takes the responsibility for renewing the timer associated to the lease 
duration, and as long as the remote participant keeps running and remains connected, all the entities within that
participant will be considered alive.

The other two kinds (MANUAL_BY_PARTICIPANT and MANUAL_BY_TOPIC) need a periodic assertion to consider the remote
participants as alive.

In this test, we are going to create a publisher and subscriber using AUTOMATIC liveliness and a lease duration value
higher than the write rate of the publisher.

**Step-by-Step**

First, launch two instances and create a publisher and a subscriber:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Select AUTOMATIC for liveliness kind.
   - Set Lease Duration to 150. (The default write rate is 75 ms)

2 - Create a square subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select AUTOMATIC for liveliness kind.
   - Set a value for the Lease Duration higher or equal to the one stated for the publisher.
     (If the value of subscriber lease duration is lower the entities don't match)

.. image:: test8_1.png
   :scale: 100 %
   :alt: Initial state
   :align: center

If you go to the *Output Tab* on Instance2, you can observe that the subscriber has recovered the liveliness once it
matches with the publisher.

Now, open the Task Manager and kill the process corresponding to the publisher (Instance1). As you can
see, the subscriber reported that liveliness was lost, as the publisher didn't terminate cleanly.

.. image:: test8_2.png
   :scale: 100 %
   :alt: State 1
   :align: center
