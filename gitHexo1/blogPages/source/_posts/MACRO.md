---
title: MARCO A High-performance Task Mapping and Routing Co-optimization Framework for NoC-based Heterogeneous Computing Systems
top: false
cover: false
toc: true
mathjax: true
date: 2021-04-27 17:34:38
password:
summary:
tags:
- MARCO
- Mapping
- Routing 
- Co-optimization
- Article
categories: Publications
---

![ Motivation  examples.  (a).  DAG  modeled  application  and  processing  rate  of  different  PEs;  (b).Computation-aware mapping and SOTA routing; (c). Communication-aware mapping and SOTA routing; (d).Co-optimized mapping and routing.](/images/marco.jpg)

## Source  
This paper published in TCAD. To refer this:  

>Hui Chen, Zihao Zhang, Peng Chen, Xiangzhong Luo, Shiqing Li and Weichen Liu, "MARCO: A High-performance Task Mapping and Routing Co-optimization Framework for Point-to-Point NoC-based Heterogeneous Computing Systems", in ACM Transactions on Embedded Computing Systems, doi: 10.1145/3476985

>Hui Chen, Zihao Zhang, Peng Chen, Xiangzhong Luo, Shiqing Li and Weichen Liu, "MARCO: A High-performance Task Mapping and Routing Co-optimization Framework for Point-to-Point NoC-based Heterogeneous Computing Systems", in Proceedings of International Conference on Compilers, Architecture, and Synthesis of Embedded Systems (ESWEEK-CASES '21), October 08-15, 2021, Virtual Event.



## Abstract 

Heterogeneous computing systems (HCSs) , which consist of various processing elements (PEs) that vary in their processing ability, are usually facilitated by the network-on-chip (NoC) to interconnect its components. The emerging point-to-point NoCs which support single-cycle-multi-hop transmission, reduce or eliminate the latency dependence on distance, addressing the scalability concern raised by high latency for long-distance transmission and enlarging the design space of the routing algorithm to search the non-shortest paths. For such point-to-point NoC-based HCSs, resource management strategies which are managed by compilers, scheduler, or controllers, e.g., mapping and routing, are complicated for the following reasons: 
- (1) Due to the heterogeneity, mapping and routing need to optimize computation and communication concurrently (for homogeneous computing systems, only communication). 
- (2) Conducting mapping and routing consecutively cannot minimize the schedule length in most cases since the PEs with high processing ability may locate in the crowded area and suffer from high resource contention overhead. 
- (3) Since changing the mapping selection of one task will reconstruct the whole routing design space, the exploration of mapping and routing design space is challenging.

Therefore, in this work, we propose MARCO, the <u>m</u>apping <u>a</u>nd <u>r</u>outing <u>co</u>-optimization framework, to decrease the schedule length of applications on point-to-point NoC-based HCSs. Specifically, we revise the tabu search to explore the design space and evaluate the quality of mapping and routing. The advanced reinforcement learning (RL)algorithm, i.e., advantage actor-critic, is adopted to efficiently compute paths.
We perform extensive experiments on various real applications, which demonstrates that the MARCO achieves a remarkable performance improvement in terms of schedule length (+44.94% ~ +50.18%) when compared with the state-of-the-art mapping and routing co-optimization algorithm for homogeneous computing systems. We also compare MARCO with different combinations of state-of-the-art mapping and routing approaches.

-----------------------------------------------------------------------

## Introduction Preview   

Nowadays, more than hundreds of processing elements (PEs) can be integrated into one system. The processing rate among different PEs varies since various application-specific integrated circuits (ASICs) are developed to assist or accelerate specific tasks. Therefore, the task mapping among PEs is of great significance due to the heterogeneous property of such heterogeneous computing systems (HCSs). Also, as the number of processing elements (PEs) integrated into one system increases, data transmission among PEs becomes the bottleneck for performance improvement, letting network-on-chip (NoC) become a promising solution for interconnecting hundreds or thousands of PEs. Moreover, the emerging point-to-point NoCs which support single-cycle-multi-hop transmission, reduce or eliminate the latency dependence on distance, addressing the scalability concern raised by high latency for long-distance transmission and enlarging the design space of the routing algorithm to search the non-shortest paths without resource contentions. Thus, the schedule length of one application runs on point-to-point NoC-based HCSs, i.e., the total time along its critical path, depends on resources management strategies, e.g., mapping and routing, which are managed by compilers, scheduler, or controllers.

![Relationship between task mapping and routing for point-to-point NoC-based HCSs.](/images/marco1.jpg) 

Mapping and routing are inter-dependent, as shown in Fig. 1, so that the co-optimization of mapping and routing is commonly proposed. In homogeneous computing systems, since PEs are with the same processing ability, the mapping would rarely influence the task execution time, targeting the communication time minimization only. 
However, HCSs, which consist of various PEs that vary in their processing ability, involve the additional design objective for mapping algorithm, i.e., computation time minimization. Thus, the co-optimization algorithm proposed for point-to-point NoC-based homogeneous computing systems cannot be directly applied for point-to-point NoC-based HCSs. To illustrate this, in Fig. 2, we generate some random task mapping and routing solutions for application H.264, which is a widely-used video compression standard, on an emerging point-to-point NoC-based HCS with the mesh size of 8x8 and heterogeneity coefficient $V_{HCS}=0.25$ (we will explain it in Section II). We illustrate the result of the co-optimization algorithm for homogeneous computing systems using the purple pentagram. Compared with the best solution among the random mapping and routing denoted by the red pentagram, the method proposed in decreases the transmission latency but ignores the execution time optimization, resulting in longer schedule length.

![Illustration of design space exploration for task mapping and routing.](/images/marco2.jpg)


Moreover, conducting mapping and routing consecutively may not achieve minimum schedule length since the PEs with high processing ability may locate in the crowded area and suffer from high resource contention overhead. In Fig. 2, we test combination of two mapping results, i.e., communication-aware and computation-aware, and the state-of-the-art (SOTA) contention minimization routing algorithm for emerging point-to-point NoCs. Specifically, the **communication-aware mapping** is the mapping result of and the **computation-aware mapping** is the mapping with the least task execution time (we will explain this in Section V). Since the routing used in the co-optimization algorithm is XY routing, using the SOTA routing algorithm further reduces the transmission time. As shown in this example, the best solution is neither the one with the minimum execution time nor the one with the minimum transmission time. Although the previous motivation example adapts point-to-point NoCs as its communication backbone, the computation and communication trade-off through mapping and routing exists in other NoC-based HCSs. Inspired by the dilemma that execution time minimization and transmission time reduction cannot be achieved at the same time, searching the optimal solution on emerging NoC-based HCSs, i.e., the minimum schedule length of applications, needs to explore the entire design space of all possible mapping and routing choices. Note that, due to the complex dependency of task mapping and routing for NoC-based HCSs, co-optimization is also meaningful for other interesting objectives, e.g., energy consumption reduction.

However, the exploration of mapping and routing design space on NoC-based HCSs is challenging. Since once we change the mapping of a single task, the entire routing solution should be modified due to the following reasons: 
- (1) At least the source or destination of one message is changed, influencing transmission of other messages. 
- (2) The execution time of that task is changed due to the different capacities of PEs, resulting in that the link usage state changes correspondingly. 

Also, the parallelism that exists in both task execution and data transmission lets the computation timeline and communication timeline overlap sometimes. Such parallelism makes the relationship of schedule length, transmission time, and execution time complex, thereby complicating the co-optimization of task mapping and routing.


In conclusion, the motivation for mapping and routing co-optimization is observed from the fact that: 
- (1) The mapping should consider task execution time (since the PEs' processing rate varies) and data communication time (since it decides the source and destination of the transmission) concurrently. 
- (2) The data communication time is unknown for task mapping due to the different performance of various routing candidates. 
- (3) For one specific mapping, the least data transmission time can be achieved is decided since the source and destination may locate in a crowded region and no NoC resource is available to transmit data. 

Thus, the co-optimization of task mapping and routing would benefit users and engineers who deploy or design applications on emerging NoC-based HCSs. In this article, the task mapping and routing are optimized simultaneously for application schedule length reduction.To the best of our knowledge, this is the first study on the co-optimization of task mapping and routing for emerging point-to-point NoC-based HCSs. The main contributions of our article are as follows:

1)
    We analyze the design space of task mapping and routing for emerging NoC-based HCSs.
    We identify that algorithms that unilaterally explore task mapping or routing cannot get the optimal solution since task mapping and routing are strongly related.
2)
    We propose MARCO, a task mapping and routing co-optimization framework for emerging NoC-based HCSs, to decrease the schedule length of applications. 
    Specifically, we revise the tabu search to explore the design space and evaluate the quality of task mapping and routing. The advanced reinforcement learning algorithm, i.e., advantage actor-critic, is adopted to compute paths efficiently.  
3)
    We perform extensive experiments on various real applications, which demonstrates that the MARCO achieves a remarkable performance improvement in terms of schedule length (+44.94% ~ +50.18%) when compared with the state-of-the-art mapping and routing co-optimization algorithm for homogeneous computing systems. We also compare MARCO with different combinations of state-of-the-art independent mapping and routing approaches.



----------------------------------

## Releted Repo
