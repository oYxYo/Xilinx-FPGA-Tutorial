### 生成reports的阶段
- after synthesis
- after implementation

### timing reports 的类型
- timing summary report
- check timing
- clock networks report
- clock interaction report
- clock domain crossing report

*timing report 用来检查 why a design fails to meet its constraints*

## 各种report的具体作用：
### 1. timing summary report
在synthesis和implementation之后自动生成。<br>
- post-implementation timing sign-off
```
report_timing_summary
```
- interactive and detailed timing analysis
```
report_timing
```
### 2. check timing
在当前的时序约束下检查ports、pins、paths，
- is my design constrained properly? are there missing constraints in the design?
```
check_timing
```
### 3. report clock networks
provides a tree view of the clock trees in the design
```
report_clock_networks
```
### 4. report utilization
resources的使用率，例如LUTs,registers,FIFOs,clocking,I/O
```
report_utilization
```
### 5. report DRC (design rule report)
```
report_drc
```
### 6. report methodology
is mandatory after implementation and prior to generating the bitstream
```
report_methodology
```
### 7. report design analysis
- timing path characteristics
- design interconnect complexity
- congestion 拥挤，阻塞
```
report_design_analysis
```
### 8. report clock interaction
analyzes timing paths that cross from one clock domain into another clock domain<br>
matrix中纵轴是source clock，横轴是destination clock
- black: no path
- green: timed path
- red: timed but unsafe path
```
report_clock_interaction
```
### 9. report CDC (clock domain crossing)
unsafe CDC could lead to metastability or data coherency issues
```
report_cdc
```
### 10. report exception
```
report_exceptions
```
### 11. report bus skew
```
report_bus_skew
```
### 12. report power
```
report_power

set_operating_conditions

set_switching_activity
```
### 13. report QoR suggestions
```
report_qor_suggestions
```


