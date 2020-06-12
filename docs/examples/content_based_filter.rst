Content Based Filter
====================

In *Fast DDS*, the data available to the subscriber can be restricted to control network and CPU usage.
The Content Based Filter can be checked when a new subscriber is deployed.
This filter draws a shaded region in the instance windows.
Only the samples that are covered by the shade will be available to the subscriber.
This region can be resized and moved dynamically.

In this test, two Publishers and two subscriber will be created, one of the latter with Content Based.

Step-by-step example implementation
-----------------------------------

First, you have to launch two instances and create a Publisher in each of them:

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 1.

2. Create an orange circle publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Publish.
   - Select CIRCLE option for Shape and ORANGE for Color.
   - Change the History field from 6 to 1.

Your windows should look similar to the following image.

.. note::

   The Instance3 shown in the image below creates a circle subscriber. Its creation will be explained later.

.. figure:: /01-figures/test6_2.png
   :alt: Initial state
   :align: center

Then, create two subscribers:

3. Create a circle subscriber:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
   - Click on Subscribe.
   - Select CIRCLE option for Shape.
   - Change the History field from 6 to 1.
   - Check Content Based.

4. Create a square subscriber:

   - Click on Subscribe in Instance3.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

In the following figure, a shaded rectangle in Instance3 is shown.
This is the filter for the samples of the Circle Shape.
If the circle is out of the rectangle, it is not available for the subscriber.

.. figure:: /01-figures/test6_3.png
   :alt: State 1
   :align: center

However, if the instance is in the rectangle, it is available for the subscriber..

.. figure:: /01-figures/test6_4.png
   :alt: State 2
   :align: center

The rectangle is configurable, i.e. it can be resized and moved dynamically.
The following images show examples of the content filter.

.. figure:: /01-figures/test4_4.png
   :alt: Publisher configuration
   :align: center

