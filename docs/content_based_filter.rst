Content Based Filter
====================

In *Fast DDS*, you can restrict the data that will be available to the subscriber to control network and CPU usage.
When  you deploy a new Subscriber, you can check the Content Based Filter.
This filter draws a shaded region in the shapes window.
Only the samples that are inside will be made available to the subscriber.
You can resize and move this region dynamically. 

In this test, we are going to create two Publishers and two Subscriber, one with Content Based.

**Step-by-Step**

First, you have to launch two instances and create a Publisher in each of them:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.
   
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
   - Change the History field from 6 to 1.
   - Check Content Based.

4 - Create a square subscriber:
   - Click on Subscribe in Instance3.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

You will see a shaded rectangle in Instance3. This is the filter for the samples of the Circle Shape.

If the circle is out of the rectangle, it is not available for the subscriber.

.. image:: test6_3.png
   :scale: 100 %
   :alt: State 1
   :align: center

On the contrary, if the instance is in the rectangle, it is available.

.. image:: test6_4.png
   :scale: 100 %
   :alt: State 2
   :align: center
   
The rectangle is configurable, you can resize and move it dynamically. The following images show examples of the 
filter.

.. image:: test4_4.png
   :scale: 100 %
   :alt: Publisher configuration
   :align: center
   
