Durability
==========

The History of the Publishers is set to KEEP_LAST. You can select the number of samples that the Publisher is going to save. 
You can also select if this History is going to be VOLATILE or TRANSIENT_LOCAL. 
The latter will send that last stored values to subscribers joining after the Publisher has been created. 

Create Publishers
-----------------

First, we have to launch three vendors and create a Publisher in each of them with the following characteristics.

+--------+--------+--------+-----------+---------+----------+------------+-----------+
| Vendor | Shape  | Color  | Partition | History - Reliable | Durability | Ownership |
+========+========+========+===========+====================+============+===========+
| **V1** | Square | RED    | NO        |     100 (ON)       | TRANSIENT  | SHARED    |
+--------+--------+--------+-----------+--------------------+------------+-----------+
| **V2** | Square | ORANGE | NO        |     100 (ON)       | TRANSIENT  | SHARED    | 
+--------+--------+--------+-----------+--------------------+------------+-----------+
| **V3** | Square | BLACK  | NO        |     100 (ON)       | TRANSIENT  | SHARED    | 
+--------+--------+--------+-----------+--------------------+------------+-----------+

The feature to keep in mind in these publishers is the "History" field. In this case, we assign a value of 100 to this field, it means that the Publisher will save the last 100 samples.

.. image:: test3_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center

Create Subscribers
------------------
   
Second, we create a Subscriber at each vendor with the following characteristics. As in Publishers, we assign a value of 100 to the History field.

+--------+--------+-----------+--------------------+------------+-----------+
|        | Shape  | Partition | History (Reliable) | Durability | Ownership |
+========+========+===========+====================+============+===========+
| **V1** | Square | No        | 100 (ON)           | TRANSIENT  | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+
| **V2** | Square | No        | 100 (ON)           | TRANSIENT  | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+
| **V2** | Square | No        | 100 (ON)           | TRANSIENT  | SHARED    |
+--------+--------+-----------+--------------------+------------+-----------+


Conclusions
-----------	

.. image:: test3_3.png
   :scale: 100 %
   :alt: Final state
   :align: center

As you can see in the previous image, we observe the last position followed by a tail with the last 99 positions published.
The value introduced in History delimits the size of this tail.
If we modify this value and we introduce a smaller value, such as 30, we will see a minor stele. (You can see that in the following image)

.. image:: test3_4.png
   :scale: 100 %
   :alt: Final state 2
   :align: center
