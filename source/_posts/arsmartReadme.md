---
title: ArSMART Manual
top: false
cover: false
toc: true
mathjax: true
date: 2021-08-31 14:59:23
password:
summary:
tags:
- ArSMART
- Manual
- ReadMe
categories: Manual
---
![Illustration of ArSMART NoC context.](/images/arsmartReadme.jpg)

Source Code link: To be public soon  

This is a simulator which enables basic NoC, SMART NoC and ArSMART NoC. This simulator is developed based on gem5. The main website can be found at http://www.gem5.org.  
<!-- more -->
---------------------------------------------------------------------------------
## To install this simulator:  
> 1. Download gem5: https://github.com/Dawnzju/gem5 (This is the version I am working on. Recommanded since the patch can be easily applied)  
> 2. Check the python version: Python 2.7.17 :: Anaconda, Inc. (conda activate py27)  
> 3. Make sure the original gem5 can be compiled and executed.  
> 4. Download and install JSONcpp: https://github.com/open-source-parsers/jsoncpp#generating-amalgamated-source-and-header  
> 5. Download NoC.patch file in this repo to gem5 folder.  
> 6. Apply this patch using command: git apply NoC.patch  
> 7. Compile again: scons build/Garnet_standalone/gem5.debug -j25 NUMBER_BITS_PER_SET=256  
---------------------------------------------------------------------------------
## To use this simulator:  
### 1. original traffic pattern for NoC are supported:  
https://www.gem5.org/documentation/general_docs/ruby/garnet_synthetic_traffic/  
### 2. Prepare the task graph file with mapping and routing information  
The task graph is saved in a json file: one task with out links is saved as:   
"9": {"total_needReceive": 93, "input_links": [], "start_time": 0, "out_links": [[[2, 93, [], [[9, "S"], [17, "S"], [25, "S"], [33, "E"], [34, "E"], [35, "E"]], 1, 9, 36], [2, 93, [], [[9, "E"], [10, "E"], [11, "E"], [12, "S"], [20, "S"], [28, "S"]], 2, 9, 36], [2, 93, [], [[9, "E"], [10, "E"], [11, "S"], [19, "S"], [27, "S"], [35, "E"]], 3, 9, 36], [2, 93, [], [[9, "E"], [10, "S"], [18, "S"], [26, "E"], [27, "E"], [28, "S"]], 6, 9, 36], [2, 93, [], [[9, "E"], [10, "E"], [11, "S"], [19, "S"], [27, "E"], [28, "S"]], 6, 9, 36]]], "end_time": 0, "visited": 0, "total_needSend": 93, "exe_time": 102, "mapto": 9}  
taskid(str):{"total_needReceive":int(total message need to be received), "input_links": list(opt,reserved for future use), "start_time": int(opt,reserved for future use), "out put links": [[link1[candidata path1: destinationTaskId,messagesize,priority(opt,reserved for future use),path,candidateCount,sourceRouter,destinationRouter],[candidata path2],[candidata path3]],[link2],[link3]],"endTime":int(opt,reserved for future use),"visited":0 or 1(opt,reserved for future use),"totalneedSend": int(total Message need to send),"exe_time":int(total task should be executed),"mapto":int(The PE has been mapped to)}  

### 3. For SMART NoC:  

| New Parameters |	Configure File |	Description	  |  
|  ----  | ----  |  ----  |
| --smart2D |	GarnetNetwork.py| Enable SMART-2D | Network.py	(experimenting)  | 
| --single-flit |	GarnetNetwork.py |	Enable Single-flit transmitting	 |
|  | 	Network.py |	(As multi-flits transmitting is not working yet)  |
| --routing algorithm |	GarnetNetwork.py | 	Set the value to 2 to enable the custom routing algorithm that follows timePoints.json	Use with --central  
            Network.py  
        example: ./build/Garnet_standalone/gem5.debug configs/example/garnet_synth_traffic.py --network=garnet2.0 --num-cpus=64 --num-dirs=64 --topology=Mesh_XY --mesh-rows=8 --sim-cycles=1000000 --single-flit --synthetic=taskgraph --smart --smart_hpcmax=4 --filename=./autocor_Mesh8x8_AIR1_XY.json  
### 4. For ArSMART NoC:  
please read this paper:  https://ieeexplore.ieee.org/abstract/document/9464312  
--central	GarnetNetwork.py	Enable the bypass at routers for the ArSMART	Use with --routing-algorithm=2  Network.py  --debug-flags=GarnetSyntheticTraffic   Print debug information   

example: ./build/Garnet_standalone/gem5.debug --debug-flags=GarnetSyntheticTraffic configs/example/garnet_synth_traffic.py --network=garnet2.0 --num-cpus=64 --num-dirs=64 --smart_hpcmax=8 --topology=Mesh_XY --mesh-rows=8 --sim-cycles=1000000 --single-flit --synthetic=taskgraph --central --filename=./autocor_Mesh8x8_AIR1_XY.json 
