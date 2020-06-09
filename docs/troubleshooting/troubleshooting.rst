Troubleshooting
===============

This document compiles the known compatibility issues with other Shapes Demo implementations and the possible solutions.

Two instances in the same computer
----------------------------------

When using eProsima Shapes Demo and RTI Shapes Demo in the same computer the file
*<Shapes Demo installation directory>/resource/xml/RTI_SHAPES_DEMO_QOS_PROFILES.xml* needs
to be modified to force RTI to only use UDPv4 as transport.
For this purpose, it is necessary to write the following lines inside the ``<qos_profile>`` element of the
RTI_Shapes_Lib::Shapes_Default_Profile.

.. code-block:: xml

   <qos_library name="RTI_Shapes_Lib">
        <qos_profile name="Shapes_Default_Profile" is_default_qos="true">
            <!-- The following lines are added to change the participant's transport protocol. -->
            <participant_qos>
                <transport_builtin><mask>UDPv4</mask></transport_builtin>
                <discovery_config>
                    <builtin_discovery_plugins>SDP</builtin_discovery_plugins>
                    <participant_liveliness_lease_duration>
                        <sec>30</sec>
                        <nanosec>0</nanosec>
                    </participant_liveliness_lease_duration>
                </discovery_config>
            </participant_qos>
            <!-- ... -->
        </qos_profile>
        <!-- ... -->
    </qos_library>

This setting is necessary to avoid the use of Shared Memory Transport.

Interoperability
================

You can see an example of the interoperability between eProsima Shapes Demo and other RTPS compliant
implementations in the following video:

https://www.youtube.com/watch?v=e9_oAJDh-tY

