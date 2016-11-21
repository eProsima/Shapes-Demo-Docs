History and Durability
======================

The History of the Publishers is set to KEEP_LAST. You can select the number of samples that the Publisher is going to save. 
The Durability QoS privides late-joining nodes with the ability to get previously sent data. You can select if Durability is going to be VOLATILE, the data samples are not stored, or TRANSIENT_LOCAL, the data samples will attempt to store in memory.

In this test we have to launch three Publisher and three Subscriber whith TRANSIENT_LOCAL. 

Finally, you will see 100 red squares on Instance2 and Instance3, mirroring the movements of the red square in the publisher of Instance1. The leading square indicates the current position of the published square. 

First, we have to launch three instances and create a Publisher in each of them:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Change the History field from 6 to 100.
   - Select TRANSIENT_LOCAL.
   
2 - Create an orange square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Publish.
   - Select SQUARE option for Shape and ORANGE for Color.
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

4 - Click Subscribe on Instance1.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.
   
5 - Click Subscribe on Instance2.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.
   
6 - Click Subscribe on Instance3.
   - Select SQUARE option for Shape.
   - Change the History field from 6 to 100.

Your windows should look similar to the following image.

.. image:: test3_3.png
   :scale: 100 %
   :alt: Final state
   :align: center

