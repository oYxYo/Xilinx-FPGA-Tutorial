## 分频时钟 generated clocks
### 产生方式：
- by clock-modifying blocks (MMCM, PLL, HSSIO). 
  - MMCM, PLL基于input primary clock生成新时钟
  ```
  create_clock -name clk_pin_p -period 5 [get_ports clk_pin_p]
  ```
  ![](https://v6.netexam.com/Courses6/Generated%20Clocks-202201272310053923/mobile/6lA7jdjeEP4_80_DX1634_DY986_CX1634_CY986.png)
  - HSSIO (high-speed serial I/O) 基于internal PLL 生成 RX CLK OUT 和 TX CLK OUT clocks
- using BUFGCE clock buffer
- using Non-Clock resources
  ```
  create_generated_clock -name <name> -source <source><relationship><objects>
  // <source> a port/pin that is asscociated with the clock to use as the reference clock
  // <relationship> 可选项：
  // divide_by<n>新时钟频率是参照时钟的n分之一; 
  // multiply_by<n>; combinaorial; invert; duty_cycle<n>
  // <objects> the list of pins/ports/nets to attach the new clock to; 
  // usually the output pin of the clock gating cell.
  ```
- **-edges** option and **-edge_shifts** option



### 命名：
the clock should be obtained through an object to which it is attached.
```
get_clocks -of_objects [get_pins clk_gen_i0/clk_core_i0/CLK_OUT]
```

### propagation：
- automatically generated clock
![](https://v6.netexam.com/Courses6/Generated%20Clocks-202201272310053923/mobile/682K9V4z7jh_80_DX1690_DY583_CX1690_CY583.png)
- manually generated clock
