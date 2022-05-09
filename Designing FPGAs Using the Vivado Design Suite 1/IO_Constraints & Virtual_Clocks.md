### 1. create appropriate input and output delays for your design

### 2. use virtual clocks for input and output delays in your design

### 3. utilize timing reports that involve inputs and outputs


### synchronous input interfaces
**synchronous communication:** the same clock is shared (common clock or related clock)<br>
**static timing path:** 

### input timing overview
the closure of setup and hold requirements of the FPGA register capturing the input data
D 数据输入； Q 输出端<br>

### output timing overview
the closure of setup and hold requirements of the downstream device capturing the output data<br>

```
set_input_delay -clock <clock name> <delay> <objects>

creat_clock -name SysClk -period 10 [get_ports ClkIn]
set_input_delay -clock SysClk 4 [get_ports DataIn]

set_input_delay -clock SysClk 4 [get_ports DataIn]
set_input_delay -clock SysClk 2 -min [get_ports DataIn]

set_input_delay -clock ClkA 3 [get_ports DataIn]
set_input_delay -clock ClkB 4 [get_ports DataIn] -add_delay
```
