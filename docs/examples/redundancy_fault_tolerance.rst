.. _examples_redundancy:

Redundancy and Fault Tolerance
==============================

*Fast DDS* allows more than one publisher to write data on the same Topic.
All publishers may have the same relevance, or one publisher can be set as the primary publisher and keep the rest as
secondary publishers.
In that case, only the main publisher can send data to the subscribers.
Please refer to
`Fast DDS OwnershipQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#ownershipqospolicy>`_
for more information on Ownership QoS.

The Ownership QoS determines if the Topic (Shape) is owned by a single publisher or not.
There are two ownership options: ``SHARE`` or EXLUSIVE ownership.
The value of a publisher's strength can be set using the ``EXCLUSIVE`` configuration.
Therefore, only the publisher with the highest strength can send data on this Topic.
If ``SHARE`` is selected, all the publishers can write data at the same time.

In this test, two publishers with ``EXCLUSIVE`` ownership in SQUARE Shape, and one subscriber with
``EXCLUSIVE`` ownership at the same Shape, will be created.

Step-by-step example implementation
-----------------------------------

First, launch two instances and create a publisher in each of them:

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Select ``EXCLUSIVE``.
   - Set Strength to 1.
   - Set Size to 15.

.. _redundancy:

2. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Select ``EXCLUSIVE``.
   - Set Strength 2.
   - Set Size to 30.

A small red square on Instance1 and a big red square on Instance2 should be displayed.

.. note::

   The Instance3 shown in the image below creates a square subscriber. Its creation will be explained later.

.. figure:: /01-figures/test5_2.png
   :alt: Initial state
   :align: center

Then, create a subscriber.

3. Create a square subscriber:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select ``EXCLUSIVE``.

A big square on Instance3 should be seen, since Instance2 has a higher strength than Instance1.

.. figure:: /01-figures/test5_3.png
   :alt: State 1
   :align: center

Response to a failure of the main publisher
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To see how the roles of the publishers change, Instance2 will be stopped.
Initially, Instance2 had higher strength and a big red square on Instance2 was observed.
However, a small red square is displayed on Instance3 since Instance1 has higher strength now.

.. figure:: /01-figures/test5_4.png
   :alt: State 2
   :align: center

Repeating the creation of a publisher with higher strength (:ref:`2. Create a red square publisher <redundancy>`),
a small red square replicating the big red square from Instance2 can be seen again.
