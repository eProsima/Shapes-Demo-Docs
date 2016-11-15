Time Base Filter
================

Time base filter can be used to specify the minimum amount of time (in milliseconds) that the Subscriber wants between updates. 

Create Publishers
-----------------

We create two Publishers with the following characteristics. Both of them can be created in the same vendor.

+--------+----------+--------+-----------+---------+----------+------------+-----------+
|        | Shape    | Color  | Partition | History (Reliable) | Durability | Ownership |
+========+==========+========+===========+====================+============+===========+
| **V1** | Square   | RED    | NO        |     1 (ON)         | VOLATILE   | SHARED    |
+--------+----------+--------+-----------+--------------------+------------+-----------+
| **V2** | Circle   | ORANGE | NO        |     1 (ON)         | VOLATILE   | SHARED    | 
+--------+----------+--------+-----------+--------------------+------------+-----------+

.. image:: test6_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center

   
Create Subscribers
------------------

Now, we create two differents Subscriber in Vendor V3, one for squares without filter, and other for circles with a time base filter of 2000 ms. 

+--------+--------+---------+--------------------+------------+--------------+
| Vendor | Shape  | Partion | History (Reliable) | Durability | Time Base    |
+========+========+=========+====================+============+==============+
| **V3** | Square | No      | 6 (ON)             | VOLATILE   | NO           |
+--------+--------+---------+--------------------+------------+--------------+
| **V3** | Circle | No      | 6 (ON)             | VOLATILE   | OK (2000 ms) |
+--------+--------+---------+--------------------+------------+--------------+

Conclusions
-----------

We can observe that square update it position continuously, but the position of the circle is uptade every 2000 ms. As you can see in the following images, V2 publishes several samples that we don't see in V3.
   
 .. image:: test7_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
  
   
