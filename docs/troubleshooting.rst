Troubleshooting
===============

This document compiles the known compatibility issues with other Shapes Demo implementations and the possible solutions.

Two instances in the same computer
----------------------------------

When using eProsima ShapesDemo and RTI Shapes Demo in the same computer the file *RTISHAPESDEMOQOSPROFILES.xml* needs to be modified to force RTI to only use UDPv4 as transport. 
You should add the following lines inside the ShapesDefaultProfile qos_profile tag.

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

This setting is necessary to avoid the use of Shared Memory as transport (disabling the loopback), a feature that is not yet implemented in Fast RTPS.
