eProsima Shape Demo 
===================

Shapes Demo is an application that Publishes and Subscribes to shapes of different colors and sizes moving on a board. 
Each Shape conforms its own topic: Square, Triangle or Circle. A single instance of the Shapes Demo can publish on or 
subscribe to several topics at a time.

It can be used to demonstrate the capabilities of eProsima Fast RTPS or as an interoperability demonstrator with other 
implementations of the RTPS protocol.


* :ref:`firststep`
* :ref:`systemtest`
* :ref:`troubleshooting`

.. _firststep:

.. toctree::
	:caption: First Stepts
	
	firststept
   
.. _systemtest:

.. toctree::
	:caption: Shapes Demo Examples
	
	discovery
	history_durability
	partition
	redundancey_fault_tolerance
        liveliness
	content_based_filter
	time_based_filter
	tcp_LAN_WAN_transport

.. _troubleshooting:

.. toctree::
	:caption: Troubleshooting
	
	troubleshooting
