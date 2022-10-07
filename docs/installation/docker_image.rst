.. _installation_docker_image:

Docker Image
============

eProsima provides the eProsima Fast DDS Suite Docker image for those who want a quick demonstration of Fast DDS running on an Ubuntu
platform. It can be downloaded from `eProsima's downloads page <https://eprosima.com/index.php/downloads-all>`_.

This Docker image was built for Ubuntu 20.04 (Focal Fossa).

To run this container you need Docker installed. From a terminal run

.. code-block:: bash

    $ sudo apt install docker.io

1.  Allow root to use graphical interface:

.. code-block:: bash

    xhost local:root

2.  Load the Docker image:

.. code-block:: bash

    docker load -i ubuntu-fastdds-suite:<FastDDS-Version>.tar

3.  Run the Docker image:

.. code-block:: bash

    docker run -it --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix \
    ubuntu-fastdds-suite:<FastDDS-Version>

4.  Launch the Shapes Demo:

.. code-block:: bash

    ShapesDemo
