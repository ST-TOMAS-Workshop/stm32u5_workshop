---- !
Presentation
----! 

# LPBAM #
## Low Power Background Autonomous Mode

*LPBAM* is an operating mode that allows peripherals to be functional and autonomous independently from power modes and without any software running. 

It is performed thanks to a hardware subsystem embedded in the STM32U5 microcontroller.

The LPBAM subsystem can chain various operations thanks to *DMA linked-list transfers*. 

The DMA operations can be:
- Autonomous peripheral configuration
- Data transfer from / to autonomous peripherals
Optionally, the LPBAM subsystem can generate asynchronous events / interrupts that can be used to:
- notify the system at the end of a subprocess or of the whole process (for example chaining another task),
- wake up the system from low-power mode,
notify the system when a functional error occurred while an LPBAM task was running.
Benefits

Two major advantages result from using LPBAM subsystem mechanisms:
- Power consumption is optimized:

Bus and kernel clocks are distributed only when needed.

Most of the product can be shut down.

Analog peripherals / oscillators are powered on only when necessary.
- CPU bandwidth is offloaded:
Peripheral configurations are done by DMA instead of CPU.

Data transfers are done by DMA instead of CPU.



![theory1](./img/01.png)
