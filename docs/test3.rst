History and Durability
======================

The History of the Publishers is set to KEEP_LAST. You can select the number of samples that the Publisher is going to save. 
You can also select if this History is going to be VOLATILE or TRANSIENT_LOCAL. 
The latter will send that last stored value to subscribers joining after the Publisher has been created. 

First, we have to launch three instances and create a Publisher in each of them:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.
   
2 - Create a blue square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select SQUARE option for Shape and BLUE for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.
   
3 - Create a black square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Publish.
   - Select SQUARE option for Shape and BLACK for Color.  
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.
   
Your windows should look similar to the following image.

.. image:: test3_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
   
Second, we create a Subscriber at each instance.

1 - Click Subscribe on Instance1.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.
   
2 - Click Subscribe on Instance2.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.
   
3 - Click Subscribe on Instance3.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.


Conclusions
-----------	

.. image:: test3_3.png
   :scale: 100 %
   :alt: Final state
   :align: center

As you can see in the previous image, we observe the last position followed by a tail with the last 99 positions published.
The value introduced in History delimits the size of this stele.
If we modify this value and we introduce a smaller value, such as 30, we will see a minor stele. (You can see that in the following image)

.. image:: test3_4.png
   :scale: 100 %
   :alt: Final state 2
   :align: center
