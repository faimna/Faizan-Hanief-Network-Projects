Redistribution by using Route-filter.

This lab demonstrates:
1. How to configure initial configuration of routers.
2. Run dynamic routing protocols (RIP and EIGRP)
3. Redistribution of Routing Protocols.
4. Route-filter.
5. Redistribution using Router-filter.
This topology consists of 40 Routers and is based on EIGRP and RIP. The purpose of this lab is to allow some networks to be redistributed while denying the others. 

The protocol or AS written alongside the loopbacks on the routers are those networks which need to be denied for the mentioned AS.

Redistribution using Route-filter is a three way step process.
Example: We have to redistribute a RIP route into EIGRP 100 and deny network 2.0.0.0/8

1. Create an ACL and deny the route which you want to redistribute.

#access-list 1 deny 2.0.0.0 0.255.255.255
#access-list 1 permit any

2. Create a box known as Route-map and call the above ACL in it.
	#Route-map ABC 1
		#match ip address 1 (ACL 1)
3. Attach the route-map while doing the redistribution
	#router eigrp 100
		#redistribute rip metric 10 10 1 1 1 route-map ABC

I have included the topology file and config files. Toplogy diagram is also included for you to create your own topology in GNS3 or any other simulation software.
Happy learning ! 


