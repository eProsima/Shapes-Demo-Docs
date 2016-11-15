Partition
=========

You can select different partitions to create groups of Publishers and Subscribers. 
In this example, you can select between four partitions (A, B, C and D). Additionally you can select the “*” partition, that will be matched against all other partitions. 

Create Publishers
-----------------

First, we must to create three Publishers with the following characteristics:

+--------+----------+--------+-----------+---------+----------+------------+-----------+
|        | Shape    | Color  | Partition | History (Reliable) | Durability | Ownership |
+========+==========+========+===========+====================+============+===========+
| **V1** | Square   | RED    | A         |     1 (ON)         | VOLATILE   | SHARED    |
+--------+----------+--------+-----------+--------------------+------------+-----------+
| **V2** | Circle   | ORANGE | B         |     1 (ON)         | VOLATILE   | SHARED    | 
+--------+----------+--------+-----------+--------------------+------------+-----------+
| **V3** | Triangle | BLACK  | (*)       |     1 (ON)         | VOLATILE   | SHARED    | 
+--------+----------+--------+-----------+--------------------+------------+-----------+

V1 will publish red squares in the partition A, V2 will publish orange circles in the partition B, and V3 will publish black triangles in all partitions.

.. image:: test4_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
   
Create Subscribers
------------------
   
Second, we create three Subscribers per vendor, one for squares in partition A, one for circles in partition A, and one for triangles in partition A. 
In the following tables we can see the characteristics of these Subcribers.
	
Subscribers in vendor V1:
	
+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **V1** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Subscribers in vendor V2:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **V2** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Subscribers in vendor V3:

+--------+----------+-----------+--------------------+------------+-----------+
|        | Shape    | Partition | History (Reliable) | Durability | Ownership |
+========+==========+===========+====================+============+===========+
|        | Square   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
| **V3** | Circle   | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+
|        | Triangle | A         | 1 (ON)             | VOLATILE   | SHARED    |
+--------+----------+-----------+--------------------+------------+-----------+

Conclusions
-----------

In partition A we only have red squares and black triangles. Because of this, all vendors find triangles and squares. 
In contrast, orange circles are published in partition B. This behaviour is shown in the following image.

.. image:: test4_3.png
   :scale: 100 %
   :alt: Publisher configuration
   :align: center
   
