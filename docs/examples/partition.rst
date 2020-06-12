.. _examples_partition:

Partition
=========

In *Fast DDS*, Partitions can be used to group subscribers and publishers.
If a publisher with a partition is deployed, only the subscriber with the same partition will receive data from it.
In this demo, there are four partitions (``A``, ``B``, ``C`` and ``D``).
Additionally, you can select the ``*`` partition, which refers to all partitions.
Please refer to
`Fast DDS Partitions Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/advanced.html?highlight=partition#wildcards-in-partitions>`_
for more information on partitions.

In this test, three publishers (Square in Partition A, Circle in Partition B, and Triangle in Partition ``*``),
and three subscribers per instance, all of them in Partition A, will be created.
Finally, red squares and black triangles in Partition A are set. Therefore, all instances are able to find
triangles and squares. However, orange circles are published in partition B and they are only visible in the
Instance2.

Step-by-step example implementation
-----------------------------------

First, we must create three publishers.

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Check Partition A.

2. Create an orange circle publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select CIRCLE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.
   - Check Partition B.

3. Create a black triangle publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Publish.
   - Select TRIANGLE option for Shape and BLACK for Color.
   - Change the History field from 6 to 1.
   - Check Partition ``*``.

Instance1 will publish red squares in the partition A, Instance2 will publish orange circles in the partition B,
and Instance3 will publish black triangles in all partitions.

.. figure:: /01-figures/test4_2.png
   :alt: Initial state
   :align: center

Then, create three subscribers per Instance with the following characteristics.

+---------------+-----------+--------------------+-----------------+-------------------+
| Shape         | Partition | History (Reliable) | Durability      | Ownership         |
+===============+===========+====================+=================+===================+
| ``Square``    | ``A``     | ``1`` (ON)         | ``VOLATILE``    | ``SHARED``        |
+---------------+-----------+--------------------+-----------------+-------------------+
| ``Circle``    | ``A``     | ``1`` (ON)         | ``VOLATILE``    | ``SHARED``        |
+---------------+-----------+--------------------+-----------------+-------------------+
| ``Triangle``  | ``A``     | ``1`` (ON)         | ``VOLATILE``    | ``SHARED``        |
+---------------+-----------+--------------------+-----------------+-------------------+

.. figure:: /01-figures/test4_3.png
   :alt: publisher configuration
   :align: center

