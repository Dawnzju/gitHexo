---
title: LAMP Manual
top: false
cover: false
toc: true
mathjax: true
date: 2021-08-31 15:20:22
password:
summary:
tags:
- ArSMART
- Manual
- ReadMe
categories: Manual
---
![Sub-message load balancing illustration. (a) Task graph before and after spliting without load balancing; (b) Task mapping and routing in NoC-basedsystem; (c) Original splitting without spliting; (d) Splitting with temporal load balancing; (e) Splitting with temporal and spatial load balancing.](/images/PMTreadme.jpg)

Source Code link: To be public soon  

# 3-DataSplitting  
This is the algorithm to generate the routing after data splitting. Please read this paper: Chen, Hui, et al. "Parallel Multipath Transmission for Burst Traffic Optimization in Point-to-Point NoCs." Proceedings of the 2021 on Great Lakes Symposium on VLSI. 2021.  
<!-- more -->
------------------------------------
## Python dependency:  
(to be continued)  
> Python 3.7.4  
> pytorch (conda activate msai)  
---------------------------
# To use this program:  
> 1. Put the json file for task graph with mapping information  
> 2. python main_autocor.py  
> 3. The result is saved in the outputs_json folder