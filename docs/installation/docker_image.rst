.. _installation_docker_image:

Docker Image
============

eProsima provides a *Shapes Demo* Docker image for those who want a quick demonstration of Fast DDS capabilities and
interoperability.
This image, based on Ubuntu 22.04, can be downloaded from
`eProsima's downloads page <https://eprosima.com/index.php/downloads-all>`_.

To run this container you need Docker installed. From a terminal, run:

.. code-block:: bash

    sudo apt install docker.io

1. Since *Shapes Demo* is a graphical application, allowing root to use the graphical interface is required:

.. code-block:: bash

    xhost local:root

2. Then, load the Docker image by running:

.. code-block:: bash

    docker load -i ubuntu-fastdds-shapes-demo\ <version>.tar

3. Finally, run the *Shapes Demo* Docker image:

.. code-block:: bash

    docker run \
        -it \
        --privileged \
        -e DISPLAY=$DISPLAY \
        -v /tmp/.X11-unix:/tmp/.X11-unix \
        ubuntu-fastdds-shapes-demo:<version>
