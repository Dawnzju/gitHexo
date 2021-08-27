---
title: ArSMART An Improved SMART NoC Design Supporting Arbitrary-Turn Transmission
top: false
cover: images/cover1.jpg
toc: true
mathjax: true
date: 2020-08-27 15:33:27
password:
summary:
tags:
- ArSMART
- Article
categories: Publications
---
![ArSMART NoC Design (a). Overview of ArSMART; (b). Cluster structure; (c). Router design.](/images/arsmart.jpg)

## Source  
This paper published in TCAD. To refer this:  

    Hui Chen, Peng Chen, Jun Zhou, L. H. K. Duong and Weichen Liu, "ArSMART: An Improved SMART NoC Design Supporting Arbitrary-Turn Transmission," in IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, doi: 10.1109/TCAD.2021.3091961. 

## Abstract 

SMART NoC, which transmits unconflicted flits to distant processing elements (PEs) in one cycle through the express bypass, is a high-performance NoC design proposed recently. 
However, if contention occurs, flits with low priority would not only be buffered but also could not fully utilize bypass. Although there exist several routing algorithms that decrease contentions by rounding busy routers and links, they cannot be directly applicable to SMART since it lacks the support for arbitrary-turn (i.e., the number and direction of turns are free of constraints) routing. Thus, in this article, to minimize contentions and further utilize bypass, we propose an improved SMART NoC, called ArSMART, in which arbitrary-turn transmission is enabled. Specifically, ArSMART divides the whole NoC into multiple clusters where the route computation is conducted by the cluster controller and the data forwarding is performed by the bufferless reconfigurable router. 
<!-- more -->
Since the long-range transmission in SMART NoC needs to bypass the intermediate arbitration, to enable this feature, we directly configure the input and output ports connection rather than apply hop-by-hop table-based arbitration. To further explore the higher communication capabilities, effective adaptive routing algorithms that are compatible with ArSMART are proposed. The route computation overhead, one of the main concerns for adaptive routing algorithms, is hidden by our carefully designed control mechanism.
Compared with the state-of-the-art SMART NoC, the experimental results demonstrate an average reduction of 40.7% in application schedule length and 29.7% in energy consumption.

-----------------------------------------------------------------------

## Introduction Preview   
With the increasing number of processing elements (PEs) integrated into one chip, the communication between PEs becomes the bottleneck for performance improvement. Based on the modified Amdahl's law which considers the effect of communication and synchronization in multi-core systems, the communication bottleneck damps the speedup gained by parallelism and computation acceleration. To support high-speed communication among PEs, network-on-chip (NoC), as a widespread communication infrastructure for large-scale many-core systems, has been refined and evolved in recent works. SMART NoC, which transmits unconflicted flits to distant PEs within one cycle through express long-distance bypass paths, is one of the most successful NoC designs. Experiments show that if every flit is magically sent from the source to its destination by using the single-cycle long-distance path, up to 85% application schedule length reduction can be achieved compared with state-of-the-art traditional NoCs. This is the “ideal” performance that SMART provides, with the optimistic assumption of single-cycle source-destination paths for all flits.


However, in practice, the actual SMART NoC performance is far away from the ideal case since the single-cycle long-distance path can hardly be built for all flits since only the winner of the arbitration among multiple long path setup requests can set up long-range links. If one packet is blocked by other packets, its bypass is broken which degrades the benefits gained by SMART NoC. Besides, the long-range path establishment is costly due to additional pipeline stages and broadcast links. To reduce wire and energy overhead of original SMART NoC, novel designs are proposed.Also, researchers try to reduce contentions from the task mapping and routing perspectives. The first work turns to task mapping which is limited by the availability of PEs and only performs well in homogeneous systems.Peng et al. try to avoid contention through XY-YX routing with intermediate nodes. However, in such design, routes for messages are not fully flexible and constrained by the number of turns.Thus, the contention issue is not fully addressed in aforementioned works.A straightforward way to significantly reduce the contentions is to relax these routing constraints and enable the data transmission of arbitrary-turn paths.


The challenge for SMART NoC to support arbitrary-turn transmission is placed by its distributed decision-making mechanism. In the start router, the route for a packet is locally computed and then a SMART-hop setup request (SSR), which carries the route information, is broadcast to the downstream routers via dedicated repeated wires to establish bypass. This local decision-making mechanism limits the routing algorithm used in SMART NoC in two aspects. 
1) With the limited area constraint and deadlock requirement, the current route computation module within the SMART NoC router is rather functionally limited, resulting in that only rule-based routing strategy (e.g., XY), which is deterministic and only allows specific turns, is applied. 
2) The SSR delivery is constrained by the dedicated wires or using specific SSR network, which does not support SSR transmission with arbitrary-turn.
Thus, even revising the original route compute unit and letting it support arbitrary-turn transmission, e.g., using the table-based method, the constrained SSR delivery is not compatible with the arbitrary-turn transmission. To support the single-cycle long-distance transmission with arbitrary-turn, centralized or cluster-based design is needed. Also, inspired by that the optimal solution is easier to be derived based on global information instead of local information, the centralized or cluster-based method could manage NoC resource (i.e., routers and links) better. 

In this article, we propose a novel NoC design based on SMART NoC, called ArSMART, which significantly decreases resource contentions and further fully utilizes bypass via our proposed mechanism of establishing arbitrary-turn paths.The main contributions of our article are as follows:  

- 1）We develop an NoC design, ArSMART NoC, to set up single-cycle long-distance paths and support arbitrary-turn data transmission, which significantly reduces resource contentions. Specifically, ArSMART divides the whole NoC into multiple clusters where the route computation is conducted by the cluster controller and the data forwarding is performed by the bufferless reconfigurable router.    
- 2）We present corresponding routing algorithms that enable ArSMART to manage NoC resources efficiently. 
Specifically, we conduct the route computation to generate a route before they demand at runtime, considering the real-time network state. The challenge to design routing algorithms for ArSMART is the difference of network states used in route computation and actual transmission. Our algorithms manage to minimize such impact and lessen contentions to improve NoC performance.  
- 3）We implement the ArSMART design and matched routing algorithms in Gem5, and conduct a full system simulation to show their effectiveness. Compared with the state-of-the-art SMART NoC, the experimental results demonstrate an average reduction of 40.7% in application schedule length and 29.7% in energy consumption.

----------------------------------

## Releted Repo
