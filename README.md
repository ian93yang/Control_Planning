# Control_Planning
control and planning for unmanned car
## 概率路线图 Probabilistic Roadmap(PRM)
## RRT 随机扩展树
（1）RRT不具备渐进最优性
（2）RRT star会在每次采样之后在采样点的周围，进行树的重新组织，对以及采样的点是否可以通过新的采样点有最短路径。
（3）informed RRT* 启发式的RRT star算法，先随着随机采样的进行在环境中找到初始的起点到终点的路径。然后以起点和终点作为焦点，以已经找到的路径长度，作为椭圆的长轴，画一个椭圆，之后的采样在椭圆内进行，循环，从而找到最优路径。


## Kinodynamic Path Finding
## State Lattice Search
1、建立移动机器人的动力学模型，对控制量进行离散化。
2、每个结点点对控制量进行采样，每个结点之间有状态转移曲线
3、缺点，在线搜索代价很大。


基于State Lattice Search的缺点，产生了混合A*算法
## Hybrid A*
Follow A* algorithm
Forward simulate states with different discrete control inputs
Keep only 1 state in state in each grid
1、对Lattice graph进行栅格化，每个网格只维护一个状态。
2、当网格中出现的新状态，使得起点到当前网格的路径更短，才将新状态代替旧状态。


## Kinodynamic RRT*
1、Follow RRT* algorithm
2、Sample a random state
3、Solve two state boundary optimal control problem 两点边界的最优控制问题


## 轨迹优化，Trajectory Optimization
### Basic Minimum-snap
给定若干点，及起点和终点

### Hrad constrained Minimun-snap 
### Soft constrained Minimun-snap 对障碍物设定距离场

## Map
### Occupancy grid map  稠密/结构化/直接坐标索引
### Octo-map            八叉树结构/稀疏/结构化/非直接坐标索引
环境中没有障碍物，用大方块，有障碍物，递归切八块
http://otomap.github.io/

### voxel hashing 哈希map->Hash table->对照表  最稀疏/结构化/直接索引
Voxel Hashing
https://github.com/niessner/VoxelHashing
InfiniTAM：
http://www.robots.ox.ac.uk/~victor/infinitam/

## Point cloud map
点云/无序/离散化/没有索引
PCL
http://pointclouds.org/

## TSDF map (Truncated Signed Distance Functions) 截断距离场
OpenChisel
http://github.com/personalalrobotics/OpenChisel

## ESDF map (Euclidean Signed Distance Functions) 关心所有的视野范围内全部距离场，轨迹优化
VoxBiox
http://github.com/ethz-asl/voxblox

FIESTA
http://github.com/HKUST-Aerial-Robotics/FIESTA

TTR's Local Map
http://github.com/HKUST-Aerial-Robotics/Teach-Repeat-Replan
全局规划 局部规划 
 
Voronoi Diagram Map  稀疏骨架/拓扑地图
http://github.com/ethz-asl/mav_voxblox_planning

## Search-based Method
Graphs have nodes and edges
undirected map 无向图
weighted map 有权重图
directed map 有向图

State sapce graph 
栅格图/概率路图
