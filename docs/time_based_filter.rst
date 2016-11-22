Time Based Filter
================

When you deploy a Subscriber in Fast RTPS, you can select a time based filter. You can restrict the number of data updates in the Subscriber with this filter. You can specify the minimum separation time (in milliseconds) between updates. Any data arriving during this interval will be discarded.

In this test, we are going to create two Publishers and two Subscribers, one with a time based filter of 2000ms. You will see that one updates its position continuously, but the other jumps every two seconds.

**Step-by-Step**

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

Your windows should look similar to the following image.

 .. image:: test7_2.png
   :scale: 100 %
   :alt: Initial state
   :align: center
  
   
