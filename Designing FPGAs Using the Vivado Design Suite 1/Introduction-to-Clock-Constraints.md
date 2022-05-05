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
