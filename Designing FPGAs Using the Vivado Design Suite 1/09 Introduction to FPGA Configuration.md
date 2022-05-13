FPGA configuration is the process of loading application-specific data into the internal memeory.<br>

## When does configuration happen
- configuration must occur **after power up**
- configuration can also occur to 重新加载另一个bitstream （same or different both okay）

## why FPGAs needs to be configured
- FPGAs are volatile by nature. 当断电后，configuration memory里存储的data全部丢失。
- 通常解决办法：把数据储存在flash memory（PROM）、disk、microprocessor、DSP processor、microcontroller、PC、board tester。

## how is the configuration mode set
via configuration pins<br>
each configuration mode has a corresponding set of interface pins<br>
### configuration pins
- DONE : high-->completion of the configuration process
- DIN: serial input for configuration data
- DOUT: daisy chains only
- CFGBVS: 
- POR_OVERRIDE: disable the default power-on-reset delay
- INIT_B
- M2, M1, M0 pins: input pins that select which configuration mode is being used
- PROGRAM_B
- CCLK
- PUDC_B

## bit file generation
- use ```write_bitstream``` command to generate a bitstream(.bit) for configuration.
- .bit file contains the configuration information from the fully-routed DCP file.
- routed DCP defines the internal logic and interconnections for the FPGA design.

## PROM file generation
- use vivado design suite to generate the bitstream files
- use the bitstream files to generate the PROM files by ```write_cfgmem``` command
- use the PROM files in programming the configuration memory device

## create a confoguration memory file
