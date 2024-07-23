# External Connectivity Using NAT or Bridge connectors in Cisco Modeling Labs

This lab demonstrates how to setup the NAT or Bridge connector to provide internet connectivity from Nodes in Cisco Modeling Labs.  The interfaces assigned to the devices are color coded to indicate which external connector they use for network access.  See the below image:

<img src="img/External Connectivity - NAT _ Bridge CML².png">

## NAT connector

The NAT interfaces are indicated by the Orange colored dots.  On the Catalyst 8000V, GigabitEthernet 1 is associated with the NAT pool, and GigabitEthernet 2 is in the 172.18.1.0/24 subnet, and uses NAT outside(G1)/inside(G2) configuration to allow that subnet to reach the internet.  Setting a statement of ip route 0.0.0.0 0.0.0.0 (nat_gw) does not work from my testing.

The management interface of the Nexus 9000v is associated 

## Bridge Connector

The bridge interfaces are indicated by the Aqua colored dots.   On the Nexus 9000v, Eth1/1 and 1/2 are assigned to VLAN 400 to provide the Ubuntu host connectivity to the internet via the bridge.  The Ubuntu host in my lab is configured with 192.168.1.205/24 and interface VLAN 400 is configured with 192.168.1.206/24 to provide ssh access to the switch.

The Cat8000v has interface GigabitEthernet 8 assigned to a management vrf, and a statically assigned address on 192.168.1.204/24.

### Notes

* The default interface behavior of the Cat8000v is to shutdown the interfaces.  Please make sure you configure the interfaces as "no shutdown" when importing the lab.

* The interfaces associated with the bridge network are assigned to the 192.168.1.0/24 subnet.  If this is your home network, please verify these addresses are available before launching.  If not these IPs are not available, or the subnet is wrong, please update the interfaces with the proper IP addressing for the lab.
