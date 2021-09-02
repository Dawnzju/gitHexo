---
title: MACRO Manual
top: false
cover: false
toc: true
mathjax: true
date: 2021-08-31 15:17:48
password:
summary:
tags:
- ArSMART
- Manual
- ReadMe
categories: Manual
---


![ Motivation  examples.  (a).  DAG  modeled  application  and  processing  rate  of  different  PEs;  (b).Computation-aware mapping and SOTA routing; (c). Communication-aware mapping and SOTA routing; (d).Co-optimized mapping and routing.](/images/marco.jpg)

Source Code link: To be public soon  

# 2-MARCO
This is the co-optimization algorithm used to generate mapping and routing solution for a given task graph. More details about this algorithm can be found in:  

--------------------------------------------------------
## Python dependency:  
(to be continued)  
> Python 3.7.4  
> pytorch (conda activate msai)  
---------------------------
<!-- more -->

# To use this program:  
1. Generate NoC description (example: N12_autocor_Mesh8x8_NoCdescription.txt)   
2. Put the task graph description file in the folder (example: N12_autocor.tgff)  
3. Adjust the hyper-parameter in main.py  
        line 29 computation_ability=CVB_method(execution=execution[1:],V_machine=0.25,num_of_rows=N)
4. Run main.py
5. Copy the final result saved in the ret.txt, for example:  
    Now is best result:
    {0: 50, 1: 13, 2: 37, 3: 30, 4: 18, 5: 46, 6: 50, 7: 17, 8: 51, 9: 47, 10: 26, 11: 2}
    {'1': {'out_links': [['2', 190, [[50, 'N'], [42, 'N'], [34, 'N'], [26, 'E'], [27, 'N'], [19, 'E'], [20, 'E'], [21, 'N']], 0, 0, -1]]}, '2': {'out_links': [['4', 70, [[13, 'S'], [21, 'E'], [22, 'S']], 0, 0, -1], ['5', 140, [[13, 'W'], [12, 'W'], [11, 'S'], [19, 'W']], 0, 0, -1], ['6', 130, [[13, 'E'], [14, 'S'], [22, 'S'], [30, 'S'], [38, 'S']], 0, 0, -1], ['7', 70, [[13, 'S'], [21, 'W'], [20, 'W'], [19, 'W'], [18, 'S'], [26, 'S'], [34, 'S'], [42, 'S']], 0, 0, -1], ['8', 60, [[13, 'S'], [21, 'W'], [20, 'W'], [19, 'W'], [18, 'W']], 0, 0, -1], ['9', 100, [[13, 'W'], [12, 'W'], [11, 'S'], [19, 'S'], [27, 'S'], [35, 'S'], [43, 'S']], 0, 0, -1], ['10', 80, [[13, 'E'], [14, 'E'], [15, 'S'], [23, 'S'], [31, 'S'], [39, 'S']], 0, 0, -1], ['11', 100, [[13, 'S'], [21, 'S'], [29, 'W'], [28, 'W'], [27, 'W']], 0, 0, -1]]}, '4': {'out_links': [['3', 70, [[30, 'W'], [29, 'S']], 0, 0, -1]]}, '5': {'out_links': [['3', 70, [[18, 'S'], [26, 'S'], [34, 'E'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '6': {'out_links': [['3', 40, [[46, 'W'], [45, 'N']], 0, 0, -1]]}, '7': {'out_links': [['3', 90, [[50, 'E'], [51, 'E'], [52, 'E'], [53, 'N'], [45, 'N']], 0, 0, -1]]}, '8': {'out_links': [['3', 50, [[17, 'E'], [18, 'E'], [19, 'E'], [20, 'E'], [21, 'S'], [29, 'S']], 0, 0, -1]]}, '9': {'out_links': [['3', 100, [[51, 'N'], [43, 'N'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '10': {'out_links': [['3', 40, [[47, 'W'], [46, 'N'], [38, 'W']], 0, 0, -1]]}, '11': {'out_links': [['3', 80, [[26, 'E'], [27, 'S'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '3': {'out_links': [['12', 210, [[37, 'W'], [36, 'W'], [35, 'W'], [34, 'N'], [26, 'N'], [18, 'N'], [10, 'N']], 0, 0, -1]]}, '12': {'out_links': []}}
6. Paste the infomation in the hand_out.py:  
    Line 84: MapResults={0: 50, 1: 13, 2: 37, 3: 30, 4: 18, 5: 46, 6: 50, 7: 17, 8: 51, 9: 47, 10: 26, 11: 2}
    Line 85: task_graph={'1': {'out_links': [['2', 190, [[50, 'N'], [42, 'N'], [34, 'N'], [26, 'E'], [27, 'N'], [19, 'E'], [20, 'E'], [21, 'N']], 0, 0, -1]]}, '2': {'out_links': [['4', 70, [[13, 'S'], [21, 'E'], [22, 'S']], 0, 0, -1], ['5', 140, [[13, 'W'], [12, 'W'], [11, 'S'], [19, 'W']], 0, 0, -1], ['6', 130, [[13, 'E'], [14, 'S'], [22, 'S'], [30, 'S'], [38, 'S']], 0, 0, -1], ['7', 70, [[13, 'S'], [21, 'W'], [20, 'W'], [19, 'W'], [18, 'S'], [26, 'S'], [34, 'S'], [42, 'S']], 0, 0, -1], ['8', 60, [[13, 'S'], [21, 'W'], [20, 'W'], [19, 'W'], [18, 'W']], 0, 0, -1], ['9', 100, [[13, 'W'], [12, 'W'], [11, 'S'], [19, 'S'], [27, 'S'], [35, 'S'], [43, 'S']], 0, 0, -1], ['10', 80, [[13, 'E'], [14, 'E'], [15, 'S'], [23, 'S'], [31, 'S'], [39, 'S']], 0, 0, -1], ['11', 100, [[13, 'S'], [21, 'S'], [29, 'W'], [28, 'W'], [27, 'W']], 0, 0, -1]]}, '4': {'out_links': [['3', 70, [[30, 'W'], [29, 'S']], 0, 0, -1]]}, '5': {'out_links': [['3', 70, [[18, 'S'], [26, 'S'], [34, 'E'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '6': {'out_links': [['3', 40, [[46, 'W'], [45, 'N']], 0, 0, -1]]}, '7': {'out_links': [['3', 90, [[50, 'E'], [51, 'E'], [52, 'E'], [53, 'N'], [45, 'N']], 0, 0, -1]]}, '8': {'out_links': [['3', 50, [[17, 'E'], [18, 'E'], [19, 'E'], [20, 'E'], [21, 'S'], [29, 'S']], 0, 0, -1]]}, '9': {'out_links': [['3', 100, [[51, 'N'], [43, 'N'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '10': {'out_links': [['3', 40, [[47, 'W'], [46, 'N'], [38, 'W']], 0, 0, -1]]}, '11': {'out_links': [['3', 80, [[26, 'E'], [27, 'S'], [35, 'E'], [36, 'E']], 0, 0, -1]]}, '3': {'out_links': [['12', 210, [[37, 'W'], [36, 'W'], [35, 'W'], [34, 'N'], [26, 'N'], [18, 'N'], [10, 'N']], 0, 0, -1]]}, '12': {'out_links': []}}
7. Run hand_out.py