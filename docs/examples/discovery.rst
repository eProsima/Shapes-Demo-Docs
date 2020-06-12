.. _examples_discovery:

Discovery and basic connectivity
================================

In *Fast DDS*, the discovery task is automatic.
*Fast DDS* performs the task of finding the relevant information and distributing it to its destination.
It means that new nodes are automatically discovered by any other in the network.
Please refer to the
`Fast DDS Discovery Documentation <https://fast-dds.docs.eprosima.com/en/latest/fastdds/discovery/discovery.html>`_
for more information on the various *Fast DDS* discovery mechanisms.

In this test, three Publishers and three Subscribers are launched.
At the end, two additional squares will be displayed in each window, reflecting the movements of the original square in
real time.
That is, subscribers subscribing to the "Square" topics are matched with the publishers of the other instances.

Step-by-step example implementation
-----------------------------------

First, three publishers must be created.

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.

2. Create a blue square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select SQUARE option for Shape and BLUE for Color.

3. Create a black square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Publish.
   - Select SQUARE option for Shape and BLACK for Color.

The current setting should be similar to that shown in the figure below.

.. figure:: /01-figures/test1_2.png
   :alt: Publish
   :align: center

Then, three subscribers must be created.

1. Click Subscribe on *Instance1*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

2. Click Subscribe on *Instance2*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

3. Click Subscribe on *Instance3*.

   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

The eProsima Shapes Demo windows should look similar to the following image.

.. figure:: /01-figures/test1_3.png
   :alt: Subscribe
   :align: center

