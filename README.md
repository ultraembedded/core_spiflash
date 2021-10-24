### SPI-Flash XIP Interface

Github:   [http://github.com/ultraembedded/cores](https://github.com/ultraembedded/core_spiflash)

This component is a basic AXI4 to SPI Flash interface (1-bit read-only mode).
Useful for executing bootloaders stored in FPGA configuration SPI PROMs.

##### Interface

| Name | Description   |
| ---- | ------------- |
| clk_i | Clock input |
| rst_i | Async active high reset |
| inport_* | AXI-4 slave interface |
| spi_clk_o | SPI master clock output |
| spi_mosi_o | SPI master data output |
| spi_cs_o | SPI master chip select (active low) |
| spi_miso_i | SPI master data input |


##### Features
* Single bit SPI Flash support (3 address cycles).
* AXI4 slave supporting singles and bursts.
* Supports SPI-Flash devices which support read page command (0x03).
* Supports CPOL=0, CPHA=0 SPI (Mode 0) only.

##### Testing
Verified under simulation and tested on FPGA (XC7A35T with N25Q64A SPI-PROM).

##### Configuration
* parameter CLK_DIV - Clock divider ratio for clk_i -> spi_clk_o (spi_clk = clk_i / (1 + CLK_DIV))
* parameter tSLCH_CYCLES - Number of clk_i cycles from chip select to SPI transfer start
* parameter tSLSL_CYCLES - Number of clk_i cycles chip select must remain in-active between transfers

##### Area (Default config, Vivado, 7 series)
- Slice LUTs:      341
- Slice Registers: 162
- BlockRAM:        0
- DSP:             0
