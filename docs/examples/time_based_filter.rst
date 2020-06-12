Time Based Filter
=================

*Fast DDS* allow the implementation of a time based filter for the subscribers.
Thus, the number of data updates in the subscriber can be restricted specifying the minimum separation time (in
milliseconds) between updates.
Any data received during this interval will be discarded.
Please refer to
`Fast DDS TimeBasedFilterQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#timebasedfilterqospolicy>`_
for more information on Time Based Filter QoS.

In this test, two publishers and two subscribers, one with a time based filter of 2000ms, will be created.
You will see that one subscriber updates its position continuously, but the other jumps every two seconds.

Step-by-step example implementation
-----------------------------------

First, launch two instances and create a Publisher in each of them:

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.

2. Create an orange circle publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select CIRCLE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.

.. figure:: /01-figures/test6_2.png
   :alt: Initial state
   :align: center

Then, create two subscriber:

3. Create a circle subscriber:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Subscribe.
   - Select CIRCLE option for Shape.
   - Check Time Based an set 2000ms.

4. Create a square subscriber:

   - Click on Subscribe in Instance3.
   - Select SQUARE option for Shape.

The eProsima Shapes Demo output should look similar to the following image.

 .. figure:: /01-figures/test7_2.png
   :alt: Initial state
   :align: center


