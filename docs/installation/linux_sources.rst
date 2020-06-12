.. _installation_linux_sources:

Linux installation from sources
===============================

For simplicity, the eProsima Shapes Demo installation manual follows the Colcon installation, since eProsima *Fast DDS*
and *Fast CDR* dependencies are downloaded and installed at the same time that eProsima Shapes Demo is built.
However, the user must assure that `Qt5 <https://doc.qt.io/qt-5/>`_ is installed.

.. _linux_colcon_installation:

Colcon installation
-------------------

To install eProsima Shapes Demo using colcon, please follow the steps below:

1.  Install the eProsima Fast DDS dependencies and verify that the system meets the installation requirements.
    The complete list of requirements and dependencies can be found in the
    `Fast DDS Linux Installation Manual <https://fast-dds.docs.eprosima.com/en/v2.0.0/installation/sources/sources_linux.html>`_.
    Specifically, follow the steps outlined in sections
    `Requirements <https://fast-dds.docs.eprosima.com/en/v2.0.0/installation/sources/sources_linux.html#requirements>`_
    and
    `Dependencies <https://fast-dds.docs.eprosima.com/en/v2.0.0/installation/sources/sources_linux.html#dependencies>`_.

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
        wget https://raw.githubusercontent.com/eProsima/ShapesDemo/master/ShapesDemo.repos
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
