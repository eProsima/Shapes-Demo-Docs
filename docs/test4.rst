Partition
=========

You can select different partitions to create groups of Publishers and Subscribers. 
In this example, there are four partitions (A, B, C and D). Additionally, you can select the “*” partition, that will be matched against all other partitions. 

First, we must create three Publishers.

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Check Partition A.
   
2 - Create an orange square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select SQUARE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.
   - Check Partition B.
   
3 - Create a black square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Publish.
   - Select SQUARE option for Shape and BLACK for Color.  
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
| **V1** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Instance2:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **V2** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Instance3:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **V3** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

In partition A we only have red squares and black triangles. Because of this, all vendors find triangles and squares. 
In contrast, orange circles are published in partition B. This behaviour is shown in the following image.

.. image:: test4_3.png
   :scale: 100 %
   :alt: Publisher configuration
   :align: center
   
