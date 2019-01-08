Partition
=========

In Fast RTPS, you can use *Partitions* to group Subscribers and Publishers. If you deploy a Publisher with a partition, only the subscriber with the same partition will receive data from it. In this demo, there are four partitions (A, B, C and D). Additionally, you can select the “*” partition, that will be matched against all other partitions.

In this test, we are going to create three Publishers (Square in Partition A, Circle in Partition B, and Triangle in Partition "*"), and three Subscribers per instance, all of them in Partition A. 

Finally, we have red squares and black triangles in partition A. Because of this, all instances are able to find triangles and squares. On the  contrary, orange circles are published in partition B and they are only visible in the Instance2. 

**Step-by-Step**

First, we must create three Publishers.

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Check Partition A.
   
2 - Create an orange circle publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select CIRCLE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.
   - Check Partition B.
   
3 - Create a black triangle publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Publish.
   - Select TRIANGLE option for Shape and BLACK for Color.  
   - Change the History field from 6 to 1.
   - Check Partition "*".

Instance1 will publish red squares in the partition A, Instance2 will publish orange circles in the partition B, and Instance3 will publish black triangles in all partitions. Your windows should look similar to the following image.

.. image:: test4_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
      
Second, create three Subscribers per Instance with the following characteristics.
	
Instance1:
	
+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **I1** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Instance2:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **I2** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Instance3:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **I3** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

.. image:: test4_3.png
   :scale: 100 %
   :alt: Publisher configuration
   :align: center
   
