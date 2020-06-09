.. _examples_lifespan:

Lifespan
==========

The Lifespan QoS establishes the maximum validity period of the samples saved on an entity's history.
When the lifespan period elapses, the corresponding sample is automatically removed.

Unlike other QoS, such as :ref:`examples_deadline` or :ref:`examples_liveliness`, this test does not provide
the means to inform the user that the sample is being removed, which makes this test more complicated to illustrate.
For this reason, two publishers and two subscribers will be created, and making only one of them use Lifespan,
the effect of using this QoS can be graphically seen.

Step-by-step example implementation
-----------------------------------

First, launch an instance and create the two publishers:

1. Create a red square publisher:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance1*).
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Select ``TRANSIENT_LOCAL`` option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Leave the Lifespan Duration to infinite.

2. Create an orange triangle publisher on the previous Shapes Demo instance:

   - Click on Publish.
   - Select TRIANGLE option for Shape and ORANGE for Color.
   - Select ``TRANSIENT_LOCAL`` option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Set Lifespan Duration to 50.

After that, change the write rate to 1000:

3. On Instance1:

    - Click on Options.
    - Select Preferences.
    - Set the update interval to 1000.

.. image:: /01-figures/test10_1.png
   :scale: 100 %
   :alt: Initial state
   :align: center

Now, create two subscribers:

4. Create a square subscriber:

   - Start eProsima Shapes Demo (this instance will be referred to as *Instance2*).
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select ``TRANSIENT_LOCAL`` option for the Durability.
   - Make sure that RELIABLE checkbox is marked.
   - Set History to 100.
   - Leave the Lifespan Duration to infinite.

5. Create a triangle subscriber:

    - Start eProsima Shapes Demo (this instance will be referred to as *Instance3*).
    - Click on Subscribe.
    - Select TRIANGLE option for Shape.
    - Select ``TRANSIENT_LOCAL`` option for the Durability.
    - Make sure that RELIABLE checkbox is marked.
    - Set History to 100.
    - Set Lifespan Duration to 50.

When a new subscriber matches with the publisher, due to the ``TRANSIENT_LOCAL`` durability, all the
samples stored on the publisher history are sent automatically to the new subscriber.

Furthermore, on Instance2 and Instance3, the square subscriber history is
filled rapidly, while the triangle subscriber is filled at the same speed as the orange triangle publisher
sends new samples. This is because in the second case, samples in the orange triangle publisher history were removed
by the QoS, and are no longer available to be sent to the subscriber, while the red square publisher history samples
were kept.

.. figure:: /01-figures/test10_2.png
   :alt: State 1
   :align: center
