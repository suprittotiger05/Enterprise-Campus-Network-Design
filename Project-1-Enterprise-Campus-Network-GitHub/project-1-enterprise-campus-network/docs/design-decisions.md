# Design Decisions

## Segmentation
Each department is assigned a dedicated VLAN to separate broadcast domains and make policy enforcement easier.

## Addressing
The lab uses four /26 subnets from `192.168.10.0/24`. This provides up to 62 usable addresses per VLAN and leaves room for lab endpoints.

## Inter-VLAN routing
Router-on-a-stick is selected for the initial design because it demonstrates 802.1Q trunking and router subinterfaces without requiring a Layer 3 switch.

## Guest isolation
An inbound extended ACL on the guest subinterface blocks guest-originated traffic to the internal department and server subnets. A production policy would require more detailed service exceptions and testing.

## Redundancy
STP is included to demonstrate loop prevention. Gateway redundancy and EtherChannel are planned extensions, not yet implemented.

## Limitations
This is a small simulated design. It does not include a production firewall, wireless controller, dual ISP, high availability, or validated capacity planning.
