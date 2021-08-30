---
title: Parallel Multipath Transmission for Burst Traffic Optimization in Point-to-Point NoCs
top: false
cover: images/cover1.jpg
toc: true
mathjax: true
date: 2020-11-20 16:50:59
password:
summary:
tags:
- Multipath Parallel Transmission
- Article
categories: Publications
---

![Illustration of hardware design. (a). Overview ofdata transmission; (b). Router design; (c) Input NI design.](/images/MPT.jpg)

## Source  
This paper published in TCAD. To refer this:  

>Hui Chen, Zihao Zhang, Peng Chen, Shien Zhu, Weichen Liu. ``Parallel Multipath Transmission for Burst Traffic Optimization in Point-to-Point NoCs.'' In Proceedings of the Great Lakes Symposium on VLSI 2021(GLSVLSI ’21), June 22–25, 2021, Virtual Event, USA.ACM, New York, NY

## Abstract 

Network-on-chip (NoC) is a promising solution to connect more than hundreds of processing elements (PEs). As the number of PEs increases, the high communication latency caused by the burst traffic hampers the speedup gained by computation acceleration. Although parallel multipath transmission is an effective method to reduce transmission latency, its advantages have not been fully exploited in previous works, especially for emerging point-to-point NoCs since: 
<!-- more -->
- (1) Previous static message splitting strategy increases contentions when traffic loads are heavy, degrading NoC performance. 
- (2) Only limited shortest paths are chosen, ignoring other possible paths without contentions. 
- (3) The optimization of hardware that supports parallel multipath transmission is missing, resulting in additional overhead. 

Thus, we propose a software and hardware collaborated design to reduce latency in point-to-point NoCs through parallel multipath transmission. Specifically, we revise hardware design to support parallel multipath transmission efficiently. Moreover, we propose a reinforcement learning-based algorithm to decide when and how to split messages, and which path should be used according to traffic loads. Experiments show that our algorithm achieves a remarkable performance improvement (+12.1% ~ +21.0%) when compared with the state-of-the-art dual-path algorithm. Also, our hardware decreases power and area consumption by 23.2% and 10.3% over the dual-path hardware.  

-----------------------------------------------------------------------

## Introduction Preview   

Network-on-Chip (NoC), as a promising solution for connecting more than hundreds of processing elements (PEs), provides high bandwidth by allowing transmitting messages in parallel. As the number of PEs increases, the high communication latency caused by the burst traffic erodes the speedup gained by parallelism and computation acceleration. Researchers have proposed their solutions to decrease NoC latency. From the hardware perspective, point-to-point NoCs transmits unconflicted flits to distant PEs using one cycle, targeting the end-to-end latency reduction. In ArSMART, authors proposed a point-to-point NoC which supports arbitrary routing and eliminates contentions at intermediate routers by adding delay at the source. From the software perspective, mapping and routing are two common ways to improve NoC performance. Although NoC resources, e.g., routers and links, are managed properly through mapping and routing, the parallelism of transmission is not fully utilized due to the unique path selection for a specific source-destination communication pair. In network communication, one communication pair can take more than one path, i.e., multipath, to transmit data to improve the transmission efficiency, inspiring researchers to apply multipath designs on NoCs.
 
 
In NoCs, initially, the multipath transmission has been proposed to reduce network congestion and traffic hotspots.Since most approaches just select one of the alternatives and send data sequentially, the high transmission latency is not fully alleviated. To further reduce latency, the simultaneous dual-path approach is proposed. This approach sends data through XY and YX paths concurrently if source and destination nodes are not in the same row or column. However, statically splitting the data into two fixed paths cannot fully exploit the advantages of parallel multipath transmission due to the following reasons. 
- (1) Static message splitting strategy without considering the NoC utilization state increases contentions when traffic loads are heavy, degrading NoC performance. 
Specifically, the dual-path algorithm indiscriminately injects up to twice of sub-messages into the NoC so that performance is dropped when encountering too much contentions.
- (2) In dual-path design, only limited shortest paths, i.e., XY and YX, are chosen with the consideration that the end-to-end latency depends on the length of the transmission path, i.e., the number of hops, in traditional NoCs. Applying XY and YX paths limits the split degree to two and ignores other possible paths that can transmit data without contentions. However, in point-to-point NoCs, the end-to-end latency dependency on distance is reduced or eliminated, enlarging the routing design space of multipath.
- (3) The optimization of hardware that supports parallel multipath transmission is missing in dual-path design, bringing large area and power overhead.

To address these problems, in this paper, we propose a software and hardware collaborated design to fully exploit the advantages of parallel multipath transmission in point-to-point NoCs. 
The main contributions of this paper are as follows:

1)
    We revised NoC router and network interface (NI) designs to support the parallel multipath transmission competently and re-order the packets from different ports with minimal overhead. 
2)
    We proposed a parallel multipath algorithm, with which, the complex problems: when to split data transmission, how to split it, and which path should be taken to transmit data, are efficiently answered through the reinforcement learning-based approach to improve the NoC performance.

 We performed extensive experiments on various real applications, which demonstrate that our algorithm achieves a remarkable performance improvement (+12.1% ~ +21.0%) when compared with the state-of-the-art dual-path algorithm. Also, our router and NI designs decrease power and area consumption by 23.2% and 10.3% over the dual-path hardware. 



----------------------------------

## Releted Repo
