.. _examples_durability:

History and Durability
======================

A publisher can send messages throughout a Topic even if there are no DataReaders on the network.
Moreover, a DataReader that joins to the Topic after some data has been written could be interested in accessing that
information.
The durability defines how the system will behave regarding those samples that existed on the Topic before the
subscriber joins.
Please refer to
`Fast DDS DurabilityQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#durabilityqospolicy>`_
for more information on Durability QoS.

In the following example, the publishers' history is set to ``KEEP_LAST``, and
there are two options for the durability configuration which are ``VOLATILE`` and ``TRANSIENT_LOCAL``.
If ``VOLATILE`` is selected, the previous data samples will not be sent.
However, if ``TRANSIENT_LOCAL`` is selected, the :math:`n^{th}` previous data samples will be sent to the late-joining
subscriber.

In this example, one hundred red squares will be displayed in *Instance2* and *Instance3*, reflecting the movements of
the red square of the publisher from *Instance1*.
The leading square indicates the current position of the published square.

Step-by-step example implementation
-----------------------------------

First, three instances are launched and a publisher is created in each of them:

1 - Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.

2 - Create an orange square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select SQUARE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.

3 - Create a black square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Publish.
   - Select SQUARE option for Shape and BLACK for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.

The eProsima Shapes Demo environment should look similar to the following figure.

.. figure:: /01-figures/test3_2.png
   :alt: Initial state
   :align: center

Then, subscriber in each instance is created.

4. Click Subscribe on *Instance1*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.

5. Click Subscribe on *Instance2*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.

6. Click Subscribe on *Instance3*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.

The eProsima Shapes Demo environment should look similar to the following figure.

.. figure:: /01-figures/test3_3.png
   :alt: Final state
   :align: center

