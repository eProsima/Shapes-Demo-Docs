Using eProsima Shapes Demo
============================

This section serves as a guide to the main menus of eProsima Shapes Demo application.
After the executable is launched, a window similar to the one presented in the following image should be displayed.

.. figure:: /01-figures/mainWindow.png
   :alt: Main Window
   :align: center

Publishing a Topic (Shape)
--------------------------

The Publish button allow the users to define the Shape (topic) and Quality of Service (QoS) for their publication.
The following image shows an example of the Publication menu.

.. image:: /01-figures/publish.png
   :scale: 100 %
   :alt: Publish Window
   :align: center

There are multiple parameters that the user can define in this menu:

- **Shape:** This parameter defines the topic where the publication is going to occur. Three different shapes can be
  published: ``Square``, ``Circle`` and ``Triangle`` (see
  `Fast DDS Topic Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/topic/typeSupport/typeSupport.html#data-types-with-a-key>`_).

- **Color:** The user can define the color of the shape. This parameter will be used as key; that is, a way to
  distinguish between multiple instances of the same shape (see
  `Fast DDS Topics with key documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/topic/typeSupport/typeSupport.html#data-types-with-a-key>`_).

- **Size:** This parameter allows to control the size of the shape. The size can vary between ``1`` and ``99``.

- **Partition:** The user can select different partitions to differentiate groups of publishers and subscribers.
  The user can select between four partitions (``A``, ``B``, ``C`` and ``D``).
  Additionally the user can select the ``*`` partition, that will be matched against all other partitions (see
  `Fast DDS Particions Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/domain/domain.html>`_).

  .. note::

    Using the wildcard (``\*``) partition is not the same as not using any partition.
    A publisher that uses the wildcard partition will not be matched with a subscriber that do not defines any
    partitions.

- **Reliable:** The user can select to disable the ``Reliable`` check-box to use a ``Best-Effort`` publisher (see
  `Fast DDS ReliabilityQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#reliabilityqospolicy>`_).

- **History and Durability:** The publishers's History is set to ``KEEP_LAST``.
  The user can select the number of samples that the publisher is going to save and whether this History is going to be
  ``VOLATILE`` or ``TRANSIENT_LOCAL``.
  The latter will send that last stored values to subscribers joining after the publisher has been created. (see
  `Fast DDS DurabilityQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#durabilityqospolicy>`_).

- **Liveliness:** The user can select the Liveliness QoS of the publisher from three different values:
  ``AUTOMATIC``, ``MANUAL_BY_PARTICIPANT`` and ``MANUAL_BY_TOPIC``. The Lease Duration value and Announcement Period
  can also be configured. The latter only applies if Liveliness is set to ``AUTOMATIC`` or ``MANUAL_BY_PARTICIPANT``
  (see
  `Fast DDS LivelinessQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#livelinessqospolicy>`_).

- **Ownership:** The Ownership QoS determines whether the key (color) of a Topic (Shape) is owned by a single
  publisher. If the selected ownership is ``EXCLUSIVE`` the publisher will use the Ownership strength value as the
  strength of its publication. Only the publisher with the highest strength can publish in the same Topic with the same
  Key
  (see
  `Fast DDS OwnershipQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#ownershipqospolicy>`_).

- **Deadline:** The Deadline QoS determines the maximum expected amount of time between samples.
  When the deadline is missed the application will be notified and a message will be printed on the console
  (see
  `Fast DDS DeadlineQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#deadlineqospolicy>`_).

- **Lifespan:** The Lifespan QoS determines the duration while the sample is still valid. When a sample's lifespan
  expires, it will be removed from publisher and subscriber histories.
  (see
  `Fast DDS LifespanQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#lifespanqospolicy>`_).

.. note::

  Using Lifespan QoS will not have any visual effect.

Subscribing to a Topic (Shape)
------------------------------

When the Subscriber button is pressed, a new window appear to allow the user to define  the Shape (topic) and
Quality of Service (QoS) for its subscription. The following image shows an example of the Subscribe menu.

.. figure:: /01-figures/subscribe.png
   :alt: Subscribe Window
   :align: center

This menu is highly similar to the Publication menu but the user cannot change the color and size of the Shape, and it
has additional elements:

- **Liveliness:** This QoS policy is applied in the same way as in the publisher except for the Announcement Period,
  which does not apply for the Subscriber
  (see
  `Fast DDS LivelinessQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#livelinessqospolicy>`_).

- **Time Based Filter:** This value can be used by the user to specify the minimum amount of time
  (in milliseconds) that the subscriber wants between updates.
  (see
  `Fast DDS TimeBasedFilterQosPolicy Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/core/policy/standardQosPolicies.html#timebasedfilterqospolicy>`_).

- **Content Based Filter:** This filter draws a rectangle in the instances window.
  Only the shapes that are included in this rectangle are accepted while the rest of them are ignored.
  The user can dynamically resize and move this content filter.

  .. note::

    Using Lifespan QoS will not have any visual effect.

Other Options
-------------

The eProsima Shapes Demo application allows the user to define additional options.
To see the Options window, please go to *Options->Preferences* in the main bar.
The following image shows the Options Menu.

.. image:: /01-figures/options.png
   :scale: 75 %
   :alt: Options Window
   :align: center

The user can customize several aspects of Shapes Demo operation:

- **Transport Protocol:** UDP is the default transport protocol for *Fast DDS* but TCP protocol is also available
  (see
  `Fast DDS Transports Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/transport/transport.html>`_).

  .. warning::

    In order to use the TCP its point-to-point connection nature must be well known: one of the Shapes Demo instance
    must be a TCP server and all the others must be TCP clients.

  To use TCP follow the next steps:

    + Push the *Stop* button in order to end UDP use. This will automatically remove all publishers and subscribers
      from this instance.

    + To create a TCP LAN server push ``TCP LAN Server`` button and fill the *Server Port* input field with an available
      port. It is the port where the application will be listening for incoming connections.

    + To create a TCP WAN server push the ``TCP WAN Server`` button:

        - Fill the *WAN IP* input field with the public IPv4 router address.
        - Fill the *Server Port* input field with an available TCP port where the application will be listening for
          incoming connections.

    .. warning::

      The router NAT and computer firewall settings must allow external connections to the server port.

    + To create a TCP client push the ``TCP Client`` button:

        - Fill the *Server IP* input field with the IP address of the server.
        - If client and server do not share the same network because the server is behind a NAT, the WAN IP address of
          the server gateway must be specified.
        - Fill the *Server port* input field with the corresponding server listening port.

    + Push the *Start* button in order to resume Shapes Demo operation.


- **Domain ID:** The user can select different Domain IDs.
  Shapes Demo instances using different Domain IDs will not communicate.
  To modify the Domain ID the user needs to stop the participant (thus removing all existing publishers and
  subscribers) and start a new one with the new Domain ID.
  See
  `Fast DDS Domain Documentation <https://fast-dds.docs.eprosima.com/en/v2.0.0/fastdds/dds_layer/domain/domain.html>`_.

- **Update interval:** This value changes the publication period for all the publishers.

- **Speed:** This scroll bar allows the user to change how much the Shape moves between two write calls.

Endpoints and Output tabs
-------------------------

A table including all created endpoints is also provided.
An example of this legend is shown in the following figure.

.. figure:: /01-figures/table1.png
   :alt: Endpoints
   :align: center

This table can be used to remove endpoints.
Two methods are provided:

- Right click in an endpoint: An option to remove the endpoint is shown.
- Pressing the delete button when the endpoint is selected.

The output tab shows the output log messages.
An example of the output tab is shown in the figure below.

.. figure:: /01-figures/table2.png
   :alt: Outputs
   :align: center
