Discovery and basic connectivity
================================

This test attemps to show the automatic discovery concept in Fast RTPS. Automatic discovery means that new applications are automatically discovered by any other members of the network. To achieve this, we need to create three publishers and three subscribers.

At the end of the test, you will see two aditional squares in each instance, mirroning the movements of the original square in real-time.

First, you have to create three publishers:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   
2 - Create a blue square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select SQUARE option for Shape and BLUE for Color.
   
3 - Create a black square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
   - Click on Publish.
   - Select SQUARE option for Shape and BLACK for Color.   
   
Your windows should look similar to the following image.

.. image:: test1_2.png
   :scale: 100 %
   :alt: Publish
   :align: center
   
Second, you have to create three subscribers:

1 - Click Subscribe on Instance1.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.
   
2 - Click Subscribe on Instance2.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.
   
3 - Click Subscribe on Instance3.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 1.

Your windows should look similar to the following image.

.. image:: test1_3.png
   :scale: 100 %
   :alt: Subscribe
   :align: center
   
