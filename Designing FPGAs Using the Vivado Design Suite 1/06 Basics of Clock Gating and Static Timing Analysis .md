**时钟门控（Clock Gating）** 是一种在数字IC设计中某些部分不需要时，关闭时钟的技术。减少耗能。<br>
**时钟使能 clock enable (CE)** 简单点说（不考虑复位信号），就是CE端控制这个DFF的输入时钟是否有效。
我们都知道DFF是靠时钟沿来采样输入信号，如果CE端为高电平1，则时钟有效，输入D会在时钟跳变时传输到Q端，而如果CE端为低电平0，则时钟无效，无论输入时钟如何跳变，输出端Q始终保持之前的值。<br>

## when to use clock gating
1. multi-cycle clock relationships exist between two regions
2. modules are not active

## how to control the clocks and implement clock gating
### 1. use local clock enables on the individual promitives (individual clock enables)
- 每个PL-synchronous element都包含一个CE，user must define logic to use the clock enable.
  PL：programmable logic(flip-flops in the CLBs, DSPs, block BRAM)
- 优点：this approach provides a great deal of control to the user
- 缺点：if some elements are clock gated while others are not, this may cause routing and utilization issues
### 2. control the clock distribution network (regional clock networks)
- 优点：maximal power savings with PL configured
- 缺点："all-or-nothing" clock distribution
