Discovery and basic connectivity
================================

This test attempts to show a basic example of publishing and subscribing with eProsima Shapes-Demo. 
We design and test with three vendors, but it is also valid with two.

Create Publishers
-----------------

First, we launch three Publishers with the following characteristics.

+--------+--------+-------+-----------+--------------------+------------+-----------+
|        | Shape  | Color | Partition | History (Reliable) | Durability | Ownership |
+========+========+=======+===========+====================+============+===========+
| **V1** | Square | RED   | NO        |       1 (ON)       | VOLATILE   | SHARED    |
+--------+--------+-------+-----------+--------------------+------------+-----------+
| **V2** | Square | BLUE  | NO        |       1 (ON)       | VOLATILE   | SHARED    | 
+--------+--------+-------+-----------+--------------------+------------+-----------+
| **V3** | Square | BLACK | NO        |       1 (ON)       | VOLATILE   | SHARED    | 
+--------+--------+-------+-----------+--------------------+------------+-----------+

The following image shows the initial state of the test.

.. image:: test1_2.png
   :scale: 100 %
   :alt: Publish
   :align: center
   
   
Create Subscribers
------------------

Second, we create a Subscriber at each vendor with these characteristics:

+--------+--------+-----------+--------------------+------------+-----------+
|        | Shape  | Partition | History (Reliable) | Durability | Ownership |
+========+========+===========+====================+============+===========+
| **V1** | Square | No        | 1 (ON)             | VOLATILE   | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+
| **V2** | Square | No        | 1 (ON)             | VOLATILE   | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+
| **V3** | Square | No        | 1 (ON)             | VOLATILE   | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+
 
The following figure shows the final state of the test. Each vendor has its square and the squares published by other vendors.

.. image:: test1_3.png
   :scale: 100 %
   :alt: Subscribe
   :align: center
   
   
