.. _examples_ros2_compatibility:

ROS 2 Compatibility
===================

As stated in the :ref:`linux_ros2_compilation` section,
eProsima Shapes Demo can be built and used on a ROS 2 installation with additional ROS 2 features.
With ROS 2 features enabled, an additional "Use ROS2 Topics" checkbox in the Participant configuration dialog will be
shown.

.. image:: /01-figures/participant_ros_enabled.png
   :scale: 100 %
   :alt: ROS 2 Participant Configuration Options
   :align: center

Enabling this box will put Shapes Demo in ROS 2 mode.
ROS 2 Shapes Demo main window changes to reflect this by showing a different title and the `Vulcanexus <https://www.vulcanexus.org/>`_ logo.

.. image:: /01-figures/ros2_shapes_demo.png
   :scale: 100 %
   :alt: ROS 2 Shapes Demo Main Window
   :align: center

.. note::
   When eProsima Shapes Demo is compiled with ROS 2, the
   `Shapes Demo TypeSupport <https://github.com/eProsima/ShapesDemo-TypeSupport>`_ (see
   :ref:`linux_ros2_compilation` compilation section) and the ROS 2 Shapes Demo executable is launched in a context with a valid ROS 2 installation sourced,
   the default value of the "Use ROS 2 Topics" checkbox will be set to true.
   Otherwise, if a valid ROS 2 installation could not be found, the checkbox will remain disabled.

When using eProsima Shapes Demo in this mode, ROS 2 will be aware of the Topics transmitted.
All topics currently known by ROS can be listed as follows:

.. code-block:: bash

   ros2 topic list -t

A typical output of the previous command with a Square created by Shapes Demo would be:

.. code-block:: bash

   /Square [shapes_demo_typesupport/idl/KeylessShapeType]
   /parameter_events [rcl_interfaces/msg/ParameterEvent]
   /rosout [rcl_interfaces/msg/Log]

Since there is a TypeSupport available for these messages, it can be used by ROS 2 to interact with the different
ShapesDemo topics.
For instance, assuming the Shapes Demo TypeSupport was built along with Shapes Demo and is currently available in the
current installation folder, a subscription to a Topic could be made like so:

.. code-block:: bash

   source ~/shapes_demo_ws/install/setup.bash
   ros2 topic echo /Square

The terminal will start showing the data transmitted on the Square topic:

.. code-block:: bash

   color: RED
   x: 175
   y: 215
   shapesize: 30
   ---
   color: RED
   x: 169
   y: 210
   shapesize: 30
   ---

Analogously, a publication could be made like this:

.. code-block:: bash

   source ~/shapes_demo_ws/install/setup.bash
   ros2 topic pub /Square shapes_demo_typesupport/idl/KeylessShapeType "{ color: BLUE, x: 155, y: 170, shapesize: 30}"

On successful execution, this is what would be shown on the terminal:

.. code-block:: bash

   publisher: beginning loop
   publishing #1: shapes_demo_typesupport.idl.KeylessShapeType(color='BLUE', x=155, y=170, shapesize=30)

The ROS 2 Shapes Demo will show the blue Square at the specified location.

.. image:: /01-figures/ros2_shapes_demo_blue_square.png
   :scale: 100 %
   :alt: ROS 2 Shapes Demo Topic CLI interaction
   :align: center

.. note::

   ROS 2 Topics enablement will disable some QoS that are not supported by ROS 2 at the moment, namely Ownership and Partitions.
   Their respective checkboxes will be disabled on the Publisher and Subscriber Dialogs.

