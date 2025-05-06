.. _installation_linux_sources:

Linux installation from sources
===============================

For simplicity, the eProsima Shapes Demo installation manual follows the Colcon installation, since eProsima *Fast DDS*
and *Fast CDR* dependencies are downloaded and installed at the same time that eProsima Shapes Demo is built.
However, the user must assure that `Qt 5 <https://doc.qt.io/qt-5/>`_ is installed.
On Ubuntu Jammy (22.04) installations, Qt 5 development packages are distributed by Canonical as an APT package and can
be downloaded by running the following on a terminal:

.. code-block:: bash

    apt update
    apt install -y qtbase5-dev

.. _linux_colcon_installation:

Colcon installation
-------------------

To install eProsima Shapes Demo using colcon, please follow the steps below:

1.  Install the eProsima Fast DDS dependencies and verify that the system meets the installation requirements.
    The complete list of requirements and dependencies can be found in the
    `Fast DDS Linux Installation Manual <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html>`_.
    Specifically, follow the steps outlined in sections
    `Requirements <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html#requirements>`_
    and
    `Dependencies <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html#dependencies>`_.

2.  Install the ROS 2 development tools (`Colcon <https://colcon.readthedocs.io/en/released/>`_ and
    `Vcstool <https://pypi.org/project/vcstool/>`_) by executing the following command:

    .. code-block:: bash

           pip install -U colcon-common-extensions vcstool

    .. note::

        If this fails due to an Environment Error, add the ``--user`` flag to the ``pip`` installation
        command.

3.  Create a `ShapesDemo` directory and download the repos file that will be used to install
    eProsima Shapes Demo and its dependencies:

    .. code-block:: bash

        mkdir -p ShapesDemo/src && cd ShapesDemo
        wget https://raw.githubusercontent.com/eProsima/ShapesDemo/master/shapes-demo.repos
        vcs import src < shapes-demo.repos

3.  Build the packages:

    .. code-block:: bash

        colcon build

4.  Link the application executable to make it accessible from the current directory:

    .. code-block:: bash

        source install/setup.bash

5.  Run eProsima Shapes Demo:

    .. code-block:: bash

        ShapesDemo

.. _linux_ros2_compilation:

ROS 2 features compilation
--------------------------

By default eProsima Shapes Demo can be built and used on a ROS 2 installation as long as an installation of Fast DDS
version 2.5.1 or higher is available and a Qt 5 installation is available.

The build process will try to locate the `Shapes Demo TypeSupport <https://github.com/eProsima/ShapesDemo-TypeSupport>`_ and, if present, will automatically enable ROS 2 compilation flags.

To download Shapes Demo and its dependencies, including the Shapes Demo TypeSupport, a different repos file, `shapes-demo-ros2.repos <https://github.com/eProsima/ShapesDemo/blob/master/shapes-demo-ros2.repos>`_, can be used.
To build eProsima Shapes Demo with ROS 2 features enabled,
follow these steps within a sourced ROS 2 Humble installation:

1.  Install the required eProsima Fast DDS dependencies and verify that the system meets the installation requirements.
    The complete list of requirements and dependencies can be found in the
    `Fast DDS Linux Installation Manual <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html>`_.
    Specifically, follow the steps outlined in sections
    `Requirements <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html#requirements>`_
    and
    `Dependencies <https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html#dependencies>`_.

2.  Install the ROS 2 development tools (`Colcon <https://colcon.readthedocs.io/en/released/>`_ and
    `Vcstool <https://pypi.org/project/vcstool/>`_) by executing the following command:

    .. code-block:: bash

        apt update
        apt install -y python3-pip wget
        pip install -U colcon-common-extensions vcstool

    .. note::

        If this fails due to an Environment Error, add the ``--user`` flag to the ``pip`` installation
        command.

3.  Create a `shapes_demo_ws` directory and download the ROS 2 version of the repos file that will be used to install
    eProsima Shapes Demo and its dependencies:

    .. code-block:: bash

        mkdir -p ~/shapes_demo_ws/src
        cd ~/shapes_demo_ws
        wget https://raw.githubusercontent.com/eProsima/ShapesDemo/master/shapes-demo-ros2.repos
        vcs import src < shapes-demo-ros2.repos

4.  Build the packages:

    .. code-block:: bash

        cd ~/shapes_demo_ws
        colcon build

5.  Link the application executable to make it accessible from the current directory:

    .. code-block:: bash

        source ~/shapes_demo_ws/install/setup.bash

6.  Run eProsima Shapes Demo:

    .. code-block:: bash

        ShapesDemo

.. note::

   When eProsima Shapes Demo is compiled with ROS 2, the
   `Shapes Demo TypeSupport <https://github.com/eProsima/ShapesDemo-TypeSupport>`_ (see
   :ref:`linux_ros2_compilation` compilation section) and the ROS 2 Shapes Demo executable is launched in a context with a valid ROS 2 installation sourced,
   the default value of the "Use ROS 2 Topics" checkbox will be set to true.
   Otherwise, the checkbox will remain disabled.
