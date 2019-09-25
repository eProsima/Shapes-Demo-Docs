Lifespan
==============================
The Lifespan QoS establish the maximum validity period of the samples saved on the entity history. Each of those
samples has a lifespan timer associated so that once it expires the linked data is removed from the entity history.

Before starting with the example, we need to advise you that it is complicated to understand.

In this test, we are going to create two Publishers and two Subscribers, one using lifespan and the other
without it, so you can see graphically the difference between both cases.

**Step-by-Step**

First, you have to launch an instance and create the two Publishers:

1 - Create a red square publisher:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Select TRANSIENT_LOCAL option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Leave the Lifespan Duration to infinite.

2 - Create an orange triangle publisher on the previous ShapesDemo instance:
   - Click on Publish.
   - Select TRIANGLE option for Shape and ORANGE for Color.
   - Select TRANSIENT_LOCAL option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Set Lifespan Duration to 50.

After that, change the write rate to 1000:

3 - On Instance1:
    - Click on Options.
    - Select Preferences.
    - Set the update interval to 1000.

.. image:: test10_1.png
   :scale: 60 %
   :alt: Initial state
   :align: center

Now, create two Subscribers:

4 - Create a square subscriber:
   - Start eProsima Shapes-Demo. (We will refer to this instance as Instance2)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select TRANSIENT_LOCAL option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Leave the Lifespan Duration to infinite.

5 - Create a triangle subscriber:
    - Start eProsima Shapes-Demo. (We will refer to this instance as Instance3)
    - Click on Subscribe.
    - Select TRIANGLE option for Shape.
    - Select TRANSIENT_LOCAL option for the Durability.
    - Make sure that RELIABLE checkbox is marked.
    - Set History to 100.
    - Set Lifespan Duration to 50.

Note that when a new subscriber matched with the publisher, due to the TRANSIENT_LOCAL durability, all the
samples stored on the publisher history are sent automatically to the new subscriber.

Knowing that we are going to explain what is happening on Instance2 and Instance3. As you can see, the square
subscriber history is fulled rapidly, while the triangle subscriber one increases at the same speed as the
orange triangle publisher sends the new samples. That's why the samples of the orange triangle publisher history
are removed faster than he sends new ones, due to the lifespan, while the red square publisher history samples
are kept.

.. image:: test10_2.png
   :scale: 60 %
   :alt: State 1
   :align: center
