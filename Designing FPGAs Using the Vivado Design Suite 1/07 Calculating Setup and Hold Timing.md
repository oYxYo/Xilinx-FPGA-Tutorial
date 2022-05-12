
data valid window = clock period - setup window - hold window<br>
start of data valid window = T_launch + T_hold<br>
end of data valid window = T_launch + T_period - T_setup<br>


![](https://v6.netexam.com/Courses6/Calculating%20Setup%20and%20Hold%20Timing-202201280715380112/mobile/5z7wL3hGpff_80_DX1621_DY986_CX1621_CY986.png)


### reg-to-reg constraints
```
create_clock
```
### input-to-reg constraints
```
set_input_delay
```
### reg-to-output constraints
```
set_output_delay
```
### input-to-output constraints
```
set_max_delay
set_min_delay
```
### timing exception
```
set_false_path
set_multicycle_path
```
### clock constraints
```
set_clock_uncertainty
jitter
set_clock_latency
set_clock_groups
```
