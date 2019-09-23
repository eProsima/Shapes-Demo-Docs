Deadline
==============================
The Deadline QoS raises an alarm when the frequency of new samples falls below a predefined threshold. This policy
can be useful for those cases which need periodical updates.

You can distinguish between the publisher and subscriber deadline period. On the publishing side, that period
defines the maximum interval between writes, while the subscriber one establishes the maximum interlude in which
the reader should receive a new sample.

In this test, we are going to create a Publisher and a Subscriber with a duration value lower than the write rate
of the publisher.

**Step-by-Step**

First, you have to launch two instances and create a Publisher and a Subscriber:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape.
   - Select RED for Color.
   - Set Deadline Duration to 50. (The default write rate is 75 ms)

2 - Create a square subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Set a value for the Deadline Duration higher or equal to the one stated for the Publisher.
     (If the value of subscriber deadline duration is lower the entities don't match)

Now, if you go to the *Output Tab* on Instance2, you can observe that both of them are continuously missing the
deadline as the value established for the duration (threshold) is lower than the publishing rate. This fact makes
that the deadline timer ends up before a new sample comes from the publisher and therefore the subscriber
shows the requested deadline missed message, while the publisher shows the offered deadline missed one.

Note that if you establish a value for requested deadline (subscriber) higher than the write rate, the requested
deadline missed message will not be printed, as the new sample arrives before the timer ends.

.. image:: test9_1.png
   :scale: 60 %
   :alt: State 1
   :align: center
