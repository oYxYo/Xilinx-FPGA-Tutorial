## what a clock is
一个振荡的周期信号（含HIGH和LOW两种状态），用来同步synchronize电路circuit中的各种信号。<br>
- period: 相邻两个上升沿之间标称时间nominal time, HIGH+LOW
- duty cycle：占空比，HIGH/PERIOD
- jitter: 时间抖动，信号周期距离其理想值偏离了多少
- phase: the starting point of the rising edge of a clock, 用来区分频率相同的不同信号

## how to create appropriate clock constraints for my design
create a clock in the **XDC** file.<br>

### using TCL command
``` tcl
create_clock -name<name> -period <period> <objects> 
create_clock -name<clk1> -period <5.0> -waveform {1.0 4.0} // default是{0.00 PERIOD/2}
```

### using GUI
- open the **Timing Constraints** window
- 双击 **Create Clock** 选项，弹出 **Create Clock** wizard
- 定义clock

### clock被创建成对象object，using TCL 来使用
```tcl
// accessing clocks
get_clocks <name> 

get_property
report_property [get_clocks <name>]
```

## set input jitter and clock latency
**system jitter:** is introduced by the clocking network inside the FPGA
```tcl
set_system_jitter <value> // set a single jitter value for all clocks in the system
```
**input jitter:** exists on the input clock, can be set independently for each clock source
```tcl
set_input_jitter <clock_name> <value> // for one specific clock
```
**latency:** an additional clock delay
```tcl
set_clock_latency -source <latency> <objects>
```
## report clocks present in the design
```tcl
report_clocks
```

## NOTES
**clock skew** 时钟偏移
- positive skew: source比destination早接收到clock
- negative skew: 反之<br>
会导致寄存器不工作<br>
if clock skew is not addressed in a design, it can result in setup and hold violations.<br>
clock pessimism is removed during the calculation of clock skew.<br>

**static timing path** is
- starts at a clocked element like a flip-flop, block RAM, DSP cell, etc.
- propagates through any number of combinatorial elements like LUTs, MUXes, and the nets that interconnect them.<br>
- ends at a clocked element.<br>

**stactic timing analysis** is a simulation method for validating the timing performance of a circuit, without simulating the full circuit but by checking all possible paths for timing violations under worst-case conditions.<br>
在vivado中，static timing engine是基于"basic elements (BELs)"的。与之相对应的，ISE软件是基于slice level的。<br>

**setup check on clock**
```
slack = PERIOD + destination_clock_delay - (source_clock_delay + data_path_delay) - clock_uncertainty

if (slack > 0) pass;
if (slack < 0) failure;
```
