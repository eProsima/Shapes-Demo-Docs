Time Based Filter
================

The time based filter can be used to specify the minimum amount of time (in milliseconds) that the Subscriber wants between updates.

First, you have to launch two instances and create a Publisher in each of them:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   
2 - Create an orange circle publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select CIRCLE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.

Your windows should look similar to the following image.

.. image:: test6_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
   
Now, create two subscriber:

3 - Create a circle subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Subscribe.
   - Select CIRCLE option for Shape.
   - Check Time Based an set 2000ms.

4 - Create a square subscriber:
   - Click on Subscribe in Instance3.
   - Select SQUARE option for Shape. 

You will see that square updates its position continously, but the circle jumps ever two secods. In this case, the publisher is only sending data once two seconds.

Your windows should look similar to the following image.

 .. image:: test7_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
  
   
