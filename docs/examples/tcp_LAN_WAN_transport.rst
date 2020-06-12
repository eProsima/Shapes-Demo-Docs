TCP Transport
==============

*Fast DDS* transport layer could be adapted to specific network requirements.
UDP transport is optimal for local network applications, but in order to interact on a Wide Area Network (WAN), where
one or several NAT mappings may be enforced, a TCP transport is more suitable.
Please refer to
`Fast DDS Transports Documentation <https://fast-dds.docs.eprosima.com/en/latest/fastdds/transport/transport.html>`_
for more information.

This section describes how Shapes Demo should be set up in order to fit some network specific layouts.

LAN configuration
-----------------

TCP over LAN can be tested in a scenario where several machines share the same LAN network;
nevertheless, UDP performs better and is the advisable choice in practical situations.
For this configuration example, one of the machines set up eProsima Shapes Demo as a server and all the others as
clients.
Assume that the server LAN IP address is ``192.168.2.49``, then
all clients instances of eProsima Shapes Demo deployed on other machines must specify this IP Server address.
In this case, the 5100 port is selected as TCP port, but any other available TCP port is valid.

.. warning::

    The server firewall must allow inbound traffic on the selected port.


.. image:: /01-figures/LAN_settings_options.png
   :scale: 100 %
   :alt: LAN settings options
   :align: center


WAN configuration
-----------------

This is the typical TCP scenario in which the server machine does not share network with its clients but its reachable
through a WAN IP address.
This may happen if the server and clients are in a different LANs of the same WAN.
To test this scenario we used the network architecture shown in the figure below.
It contains the following elements:

*   A Main Router which simulates the WAN network.
    In this network Router C has address ``192.168.1.74`` and Router S has address ``192.168.1.75``.
*   A client LAN network managed by Router C.
*   A server LAN network managed by Router S.
    The Router S NAT settings relay any inbound TCP traffic to port 5100 towards Sever machine.
    The TCP port 5100 was arbitrarily chosen, any available port will do.
*   An eProsima Shapes Demo client running in the machine with IPv4 address ``192.168.2.17``.
*   An eProsima Shapes Demo server running in the machine with IPv4 address ``192.168.3.49``.
    The Server machine firewall settings allow inbound TCP traffic to port 5100.

.. figure:: /01-figures/WAN_network_layout.png
   :alt: WAN test layout
   :align: center

The previous configuration (see `LAN configuration`_) does not work in this network scenario because server and client
are behind a NAT.

The following image shows server and client settings:

*   On the client side, the *server IP* field contains the server's router IP address, i.e. the Router S IP address
    (``192.168.1.75``).
    The client's router can understand this address and properly lead the outbound traffic.
*   On the server side, the *WAN IP* field contains the server's router IP address, i.e. i.e. the Router S IP address
    (``192.168.1.75``) since Router S NAT settings relay inbound traffic to server's TCP port towards Server computer.

.. figure:: /01-figures/WAN_settings_options.png
   :alt: WAN settings options
   :align: center

