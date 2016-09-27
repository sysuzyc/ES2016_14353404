# Energy-Efficient MAC

1. contention-based
2. TDMA
3. hybrid
4. cross layer protocols

communication module consume most energy <-- main optimization goal
MAC directly control communication module

## contention-based

core idea: when one node needs to send data, it will compete for wireless channel. Contention-based protocols require no coordination among the nodes accessing the channel. Colliding nodes will back off for a random duration of time before attempting to access the channel.

##### 1.1 S-MAC  

IEEE 802.11 divide the time into frames whose length is determined by application. There are work stage and sleep stage in a frame. Periodical listening and sleeping.
Advantages:

1. the neighbor nodes reduce the idle listening by constructing a virtual cluster through consistency sleep schedule of negotiate mechanism;
2. reduce the transport delay by adopting traffic adaptive listening mechanism;
3. use beacoms to reduce retransmission and avoid listening to unnecessary data
4. reduce the control packet overheads and packet dalay through message division and burst transmission

Disadvantages: 

1. period length is limited by delay and cache size; 
2. the active time depends on message transmission rate; 
3. the active time must adapt to highest traffic load to guatantee reliable and timely message transmission;
4. idle listening will relativly increase when traffic load is low.

##### 1.2 T-MAC

Improvement to S-MAC to reduce energy consumption on idle listening.
It introduces an adaptive duty cycle: all messages are transmitted in variable length bursts and the lengths of bursts are dynamically determined.
active period and sleep period
disadvantage: early sleeping problem

##### 1.3 U-MAC

based on SMAC and provides three main improvements on this protocol : 

	a) various duty-cycles;
	b) utilization based tuning of duty-cycle;
	c) selective sleeping after transmission

1. various duty - cycles

   ​	various duty-cycles are assigned for different nodes. Nodes have to exchange their schedules and synchronize clock with neighbors with fixed period.

2. utilization based tuning of duty-cycle

   ​	utilization based tuning of duty-cycle reflection to different traffic loads of every node in a network.

   ​	Such variation correspond to the diversity of performed tasks by a particular node and its location.

3. selective sleeping after transmission

   ​	selective sleeping after transmission avoid unnecessary energy wastage.



##### Conclusion for contention-based MAC protocol:

Advantages:

​	a) have good scalability

​	b) support node changes and new node inclusion well

​	c) These protocaols adopt different mechanisms to reduce energy waste on collision, idle listening ,overhearing.

However:

​	The energy efficiency of contention-based MAC-layer protocols remain low due to collision,  idle listening  and excessive control overhear inevitable.



## TDMA-based MAC

Scheduling-based TDMA techniques offer an inherent collision-free scheme by assigning unique time slots for every node to send or receive data.

Advantage of TDMA

​	a) Interference between adjacent wireless links is guaranteed to be avoided.  Thus, no energy wasting comes from packet collision.

​	b) TDMA can solve the hidden terminal problem without extramessage overhead. 



##### 2.1 μ-MAC 

​	Obtain high sleep ratio while preserving the message latency and reliability at acceptable level.

​	Adoption of a schedule-based approach to access to the shared medium, and by assumption of traffic behavior predictability.

Disadvantage:

- Incur large overhead
- Has to take place frequently, which is impossible to adapt it to frequent network organization changes.
- Furthermore, the knowledge of the traffic pattern has to be available.



##### 2.2 DEE-MAC

​	For energy consumption reduction by forcing the idle listening nodes to sleep using synchronization performed at the cluster head.

​	DEE-MAC operations consist of rounds.

###### Disadvantage:

​	The power of cluster head is easily depleted so the network partitions happen easily.



##### 2.3 SPARE MAC

​	<u>Save energy through limit the impact of idle listening and traffic overhearing.</u>

​	The protocol dramatically decrease collisions and idle listening.

###### Disadvantage:

-  The control packet overhead is very large	
-  The data delay is very large.

        ​

##### Conclusion for TDMA-based mac

 advantages:

1. avoid collision



disadvantages:

1. Cluster is difficult to dynamically change its frame length and time slot assignments, which contributes to poor scalability.
2. The requirements on cluster head are higher than ordinary sensor nodes, especially power and computation capability.
3. Need strict time synchronization which results in high cost on hardware and high latency for data.



## Hybrid Contention-based and TDMA-BASED MAC

combine the advantages of contention-based MAC with TDMA-based MAC.

Two main part:

1. Control packets are sent in the random access channel.
2. Data packets are transmitted in the scheduled channel.

Advantages:

​	The hybrid propocols can gain high energy savings and offer better scalability and flexibility 

Main hybrid protocols:

Z-MAC, A-MAC, IEEE 802.15.4

##### 3.1 Z-MAC

​	An integration of TDMA(time division multiple access) and CSMA (Carrier Sense Multiple Access), which uses CSMA as the baseline with a TDMA schedule as a 'hint' to improve contention resolution.

​	Two basic components:

	1. neighbor discovery and slot assignment
	2. local framing and synchronization.

###### Disadvantage:

​	it needs to implement global clock synchronization once at the setup phase.

​	

##### 3.2 A-MAC

​	A hybrid of CSMA and TDMA protocol, proposed recently for sensor network aiming at providing collision-free, non-overhearing and less idle-listening transmission services.

​	Mainly design for long-term surveillance and monitoring application.



##### 3.3 IEEE 802.15.4

​	For low-rate Wireless Personal Area Networks(WPAN).

​	super-frame structure.

​	TDMA-based period for guaranteed access and contention-based period for non-guaranteed access.

​	No special design for energy conservation except a typical duty cycle controlling scheme.



##### Conclusion for hybrid

- Control packet overhead is large.

- energy waste in transition between two operation modes is high.

- High latency is introduced due to transition between the two mechanisms.

  ​

## Cross layer MAC focused on energy efficiency

Consider the correlation of layers in WSN.

​	In a cross layer design of the use of **forward error correction(FEC)** coding and the determination of the awake/sleep periods for narrowband wireless sensor networdks is presented.

​	A new cross layer MAC protocol was presented in called MAC-CROSS, which improved energy efficiency by making use of interaction between **MAC layer and routing layer**.

​	In the MAC-CROSS algorithm, routing information at the network layer is utilized for the MAC layer so that it can **maximize sleep duration of each node**.



MAC layer is influenced by other layer.

- Physical layer affects the MAC by changing its transmission power and modulation. 
- Routing layer chooses proper wireless links to relay packets to the destination so the routing decision will change the contention level at the MAC layer.
- Congestion and rate control in the transport layer will change the traffic volume in each communication link while traffic types will have great effect on MAC layer.
- Need more research in depth



## Conclusion

MAC protocol is the major determining factor in WSN energy performance.

​	Whatever contention-based MAC or TDMA-based MAC is still wasteful in eneergy and they could not adapt to the dynamic traffic well. 

- Contention-based MAC waste energy by <u>idle lestening and large control packet overhead</u>.
- TDMA protocols need to keep <u>strict clock synchronization among nodes</u>.
- The hybrid MAC <u>intergrating the two kinds of mechanisms</u> is better in energy efficiency.However, it is <u>complex in transition mechanisms</u>.
- Cross layer <u>make full use of information in protocol stack</u> and <u>reduce energy consumption dramatically</u>. However, cross layer method <u>could significant increse the design complexity</u> and <u>diminish the advantages of layer method</u>.

