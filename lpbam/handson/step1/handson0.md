# Hands On Overview

In LPBAM Handson we will implement the following scenario making use of **two queues**.

- ADC4 conversion will be triggered by LPTIM1 at 256Hz for 1s.
- ADC4 converts data samples that are transferred to SRAM by LPDMA in STOP2 mode
- After 1s we change the LPTIM frequency to trigger 64Hz conversion rate for 1s
- LPDMAch1 will be used for memory to periph transfer and LPDMAch0 for LPTIM reconfig keeping MCU in Stop2
- Wakeup will happed on DMA TC triggered by ADC4 when 320 data words are acquired

<ainfo>
Same application can also run on a single queue, our purpose it to show how to handle multiple LPDMA channels and how complexity is reduced thanks to LPBAM configurator
</ainfo>

![Cubemx start](./img/0001.png)

## Queue 1

![Cubemx start](./img/0002.png)
 

 ## Queue 2
 ![Cubemx start](./img/0003.png)