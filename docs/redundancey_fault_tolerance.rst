Redundancy and Fault Tolerance
==============================

Fast RTPS allows more than one Publisher to write data on the same Topic. You can allow all Publishers to have the 
same relevance, or you can set one as the primary Publisher and keep the rest as secondary Publisher. In that case, 
only the main Publisher can send data to the subscribers.

The Ownership QoS determines if the Topic (Shape) is owned by a single Publisher or not. 

You can select SHARE or EXLUSIVE ownership, if you select EXCLUSIVE for a publisher, you have to indicate the value 
of strength for it. Only the Publisher with the highest strength can send data on this Topic. If the primary Publisher 
has a problem and cannot write data, the secondary Publisher with the highest strength is promoted to primary Publisher. 
If you select SHARE, all the publishers can write data at the same time.

In this test, we are going to create two Publishers with EXCLUSIVE ownership in SQUARE Shape, and one Subscriber with 
EXCLUSIVE ownership at the same Shape.


**Step-by-Step**

First, you have to launch two instances and create a Publisher in each of them:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Select EXCLUSIVE.
   - Set Strength to 1.
   - Set Size to 15.
   
2 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   - Select EXCLUSIVE.
   - Set Strength 2.
   - Set Size to 30.

You should see a small red square on Instance1 and a big red square on Instance2.

.. image:: test5_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
  
Now, create a Subscriber.

3 - Create a square subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select EXCLUSIVE.

You should see a big square on Instance3, because Instance2 has a higher strength than Instance1.

.. image:: test5_3.png
   :scale: 100 %
   :alt: State 1
   :align: center


*Failure*

Now you have to stop Instance2. Initially, Instance2 had higher strength and you saw a big red square on Instance2, 
but you should see a small red square because Instance1 has higher strength now.

.. image:: test5_4.png
   :scale: 100 %
   :alt: State 2
   :align: center

If you repeat the second step, you should see a big red square mirroring the big red square movements in Instance2 
again.
