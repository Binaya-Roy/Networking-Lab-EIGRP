# Networking-Lab-EIGRP

EIGRP is a dynamic routing protocol that helps routers automatically find the best path and update routes quickly when the network changes. It is classless, supports VLSM/CIDR, and is known for fast convergence and efficient bandwidth use.

In EIGRP, max load balance means the maximum number of equal-cost paths the router can use for one destination. By default, Cisco EIGRP usually supports 4 paths, and you can increase it with the maximum-paths command.

Short detail

•	EIGRP stands for Enhanced Interior Gateway Routing Protocol.

•	It uses the DUAL algorithm to choose loop-free routes and recover quickly from failures.

•	It sends partial updates instead of the full routing table every time, which saves bandwidth.

•	It supports unequal-cost load balancing, which can use multiple paths intelligently.

•	It can go up to 100 hops.

In EIGRP, AS means Autonomous System. It is just the group number that tells routers which EIGRP network they belong to, and routers must use the same AS number to become neighbors.
Think of it like a team number for EIGRP routers. If two routers have different AS numbers, they will not exchange EIGRP routes with each other.

Core ideas

•	EIGRP is a dynamic routing protocol that learns routes automatically and converges quickly when a link fails.

•	It uses the DUAL algorithm to pick the best path and keep backup paths ready.

•	It supports VLSM/CIDR, so it works well with subnetted networks.

Key terms

•	AS means Autonomous System, and both routers must use the same AS number to become neighbors.

•	Successor is the best route, and feasible successor is the backup route.

•	Metric is mainly based on bandwidth and delay by default.

Useful features

•	It sends partial updates instead of full routing tables, which saves bandwidth.

•	It supports equal-cost and also unequal-cost load balancing using variance.

•	It uses multicast address 224.0.0.10 for EIGRP neighbors.

Common lab issues

•	Same AS number is required.

•	K-values must match on all neighbors.

•	Interfaces can fail to form neighbors if they are passive, down, or filtered by ACLs.

•	Auto-summary can cause problems in discontiguous networks, so many labs use no auto-summary.

LAB CONFIGURATION

Router

1.	Access Router:

• Enter privileged EXEC mode (to run advanced commands):

enable

• Enter global configuration mode (to make configuration changes):

configure terminal

2.	Configure Interface IP Address:

• Enter interface configuration mode :

interface Ethernet0/0

• Set IP address and subnet mask: 

ip address 192.168.12.1 255.255.255.252

• Enable the interface (if it’s administratively down):

No shutdown

Configure all the router interface in similar way.

3.	Save Configuration:

• Save the current configuration to startup-config (to retain changes after reboot):

write 

Or: copy running-config startup-config

4.	Exit Router Mode:

• Exit to previous mode:

exit 

Or: Cltr z

RIP routing command:

router eigrp 10

 network 192.168.10.0
 
 network 192.168.12.0
 
 network 192.168.13.0
 
 no auto-summary 

All the directly connected network of each router should be configured.

(Include all the ip address that is not directly connected) Configure all the router interface in similar way.

Router

Configure PC IP address:

ip 192.168.10.2/24 192.168.10.1

save

• Check PC IP address:

Show ip

• Configure all the pc’s interface in similar way.

Ping test result:
 
Trace route result:
 
