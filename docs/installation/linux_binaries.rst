.. _installation_linux_binaries:

Linux installation from binaries
================================

The following explains how to launch the eProsima Shapes Demo application on Linux systems running Ubuntu OS without
the need for compilation. To do this, a Docker image will be used.

1.  Download and install Docker application. Open a terminal and type the following command:

    .. code-block:: bash

        sudo apt-get install docker.io

2.  Download the Docker image file from https://eprosima.com/index.php/downloads-all.

3.  Allow root to use graphical interface:

    .. code-block:: bash

        xhost local:root

4.  Load the Docker image:

    .. code-block:: bash

        docker load -i ubuntu-fast-dds-shapesdemo_2.0.0.tar

5.  Run the Docker image:

    .. code-block:: bash

        docker run -it --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ubuntu-fast-dds-shapesdemo:v2.0.0


