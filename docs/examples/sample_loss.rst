.. _sample_loss:

UDP Sample Loss modality
========================

*Fast DDS* allows creating a publisher that can intentionally drop a percentage of samples.
This feature allows the user to simulate network conditions where a certain amount of data loss occurs.
The percentage of samples to be lost can be configured by the user.

In this test, one Publisher and one Subscriber are launched.
At the end, the light squares displayed in each window, reflecting the movements of the original square in real time,
will be spaced further apart indicating sample loss of 60%.
That is, subscriber subscribing to the "Square" topics are matched with the publisher of the other instance.

Step-by-step example implementation
-----------------------------------

1. Create a participant:

   - Start eProsima Shapes Demo.
   - Click on Options > Participant Configuration.
   - Select Enable UDP Sample Loss.
   - Select OK in the Popup window.
   - Insert 60 as percentage of loss.

The Popup window will appear like shown in the figure below.

.. figure:: /01-figures/test11_1.png
   :alt: Partic
   :align: center

2. Create a red square publisher:

   - Click on Publish.
   - Select SQUARE option for Shape and RED for Color.

3. Create a red square subscriber:

   - Click on Subscribe.
   - Select SQUARE option for Shape and RED for Color.

Then, the subscriber will be created.

The eProsima Shapes Demo windows should look similar to the following image.

.. figure:: /01-figures/test11_2.png
   :alt: Subscribe
   :align: center
