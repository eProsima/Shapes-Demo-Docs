.. _examples_liveliness:

Liveliness
==========

The Liveliness QoS can be used to ensure whether specific entities are alive or not.
There are three values to specify the liveliness' kind: ``AUTOMATIC``, ``MANUAL_BY_PARTICIPANT`` or ``MANUAL_BY_TOPIC``
liveliness.
If any of the first two is selected, a value for the lease duration and announcement period can be set.
However, if ``MANUAL_BY_TOPIC`` is selected, only the lease duration can be configured, as the announcement period is
not used with this configuration.

With the ``AUTOMATIC`` liveliness kind, the service takes the responsibility for renewing the timer associated to the
lease duration, and as long as the remote participant keeps running and remains connected, all the entities within that
participant will be considered alive.

The other two kinds (``MANUAL_BY_PARTICIPANT`` and ``MANUAL_BY_TOPIC``) need a periodic assertion to consider the remote
participants as alive.

In this test, a publisher and subscriber using ``AUTOMATIC`` liveliness will be created, and a lease duration value
higher than the write rate of the publisher will be set.

Step-by-step example implementation
-----------------------------------

First, launch two instances and create a publisher and a subscriber:

1. Create a red square publisher:

   - Start eProsima Shape Demo. (We will refer to this instance as Instance1)
   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.
   - Select ``AUTOMATIC`` for liveliness kind.
   - Set Lease Duration to 150. (The default write rate is 75 ms)

2. Create a square subscriber:

   - Start eProsima Shape Demo. (We will refer to this instance as Instance2)
   - Click on Subscribe.
   - Select SQUARE option for Shape.
   - Select ``AUTOMATIC`` for liveliness kind.
   - Set a value for the Lease Duration higher or equal to the one stated for the publisher.
     (If the value of subscriber lease duration is lower the entities do not match)

.. figure:: /01-figures/test8_1.png
   :alt: Initial state
   :align: center

On the *Output Tab* of Instance2, it can be observed that the subscriber has recovered the liveliness once it
matches with the publisher.

Then, kill the process corresponding to the publisher (Instance1).
It can be seen that the subscriber reported that liveliness was lost, as the publisher did not terminate cleanly.

.. figure:: /01-figures/test8_2.png
   :alt: State 1
   :align: center
