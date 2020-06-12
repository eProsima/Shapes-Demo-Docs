.. _examples_deadline:

Deadline
========

The Deadline QoS raises an alarm when the frequency of new samples falls below a predefined threshold.
This policy can be useful for those cases which need periodical updates.
There exists a distinction between publisher and subscriber deadline period.
On the publisher side, that period defines the maximum interval between writes, while on the subscriber's, it
establishes the maximum interval in which the reader expects to receive a new sample.
Please refer to
`Fast DDS LivelinessQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#livelinessqospolicy>`_
for more information on Liveliness QoS.

In this test, a publisher and a subscriber with a deadline period higher than the write rate
of the publisher will be created.
That shows the normal behavior of the system.
Then the write rate will be increased to illustrate the effects of non-compliance with the deadline.

Step-by-step example implementation
-----------------------------------

First, launch two instances and create a publisher and a subscriber:

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape.
   - Select RED for Color.
   - Set Deadline Duration to 100. (The default write rate is 75 ms)

2. Create a square subscriber:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Set a value for the Deadline Duration higher or equal to the one stated for the publisher.

   .. warning::

      If the value of the subscriber Deadline Duration is lower than the value stated for the publisher
      the entities will not match.

In the following figure, the normal behavior of the system can be seen, where the publisher is sending new samples and
the subscriber is receiving them before the deadline expires.

.. figure:: /01-figures/test9_1.png
   :alt: State 1
   :align: center

Now, increase the write rate:

3. On Instance1:

   - Click on Options.
   - Select Preferences.
   - Set the update interval to 200.

.. figure:: /01-figures/test9_3.png
   :alt: State 2
   :align: center


On the *Output Tab* can be observed that both publisher and subscriber are continuously missing the deadline,
as the value established for the deadline period is lower than the publishing rate.

.. figure:: /01-figures/test9_4.png
   :alt: State 2
   :align: center
