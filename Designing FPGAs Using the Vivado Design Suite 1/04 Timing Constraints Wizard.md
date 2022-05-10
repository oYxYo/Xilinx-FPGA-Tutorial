### three steps to create constraints
- create clocks and clock interactions
- set input and output delays
- set timing exceptions

master/primary clock创造一个时间坐标系，generated clock属于这个clock domain<br>
**forward clock** are generated clocks defined on *output ports* that replicate internal clocks. It is usually a time reference for other output ports to form a source-synchronous interface.<br>
**external feedback delay**是input&output ports之间的board delay。both min and max delay values must be specified.


### 时钟管理器CMT clock management
- PLL就是锁相环，时钟倍频，分频，调节相位等都是可以用PLL
- MMCM是混合模式时钟管理器，是在PLL的基础上加上了相位**动态**调整功能，因为PLL是模块电路，而动态调相是数字电路，所以叫混合模式。

7s FPGA中，最高包含了24个CMT，每个CMT包含一个MMCM和一个PLL。Ultrascale中，一个CMT包含一个MMCM和两个PLL。<br>

### combinational delays
```tcl
set_max_delay
set_min_delay
```

### exclusize clocks
- physically exclusive clock groups: same sourece point, same clock tree
- logically exclusive clock groups: different source points, share part of their clock tree
