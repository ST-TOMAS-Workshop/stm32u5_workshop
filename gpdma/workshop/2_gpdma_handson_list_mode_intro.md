----!
Presentation
----!

# GPDMA handson adding features

## Our goal

* Setup ADC to 
  * convert 4 channels in circle
  * generate DMA requests
* Set GPDMA with linked list
  * To get data from ADC
  * Transfer them to buffer
* Which allows us to later add more lists in later steps

# Classic DMA circular mode

Classical DMA had a bit, which allows repeat the configuration.
When DMA finished it automatically reload the previous configuration.

![old circular](./img/old_dma_circular.json)

# GPDMA list mode

The GPDMA have different approach
It have **lists** containing **configuration nodes** which are used by **GPDMA**.

When GPDMA ends it looking for new node configuration based on **LLR** register. If is found it reload own registrs with it also with new LLR.
This configuration is called **NODE**. Multiple nodes are **queue** making list. 

<ainfo>
LLR is Linked list register
Contain position of nest GPDMA node
</ainfo>

![gpdma list](./img/gpdma_list.json)

# The GPDMA will use nodes for those registers: 

In our case each linked list node will update this GPDMA registers.
After previous GPDMA node is finished. 

TR1 - Transfer register 1
TR2 - Transfer register 2
BR1 - blck register 1
SAR - Source address register 
DAR - Destination address register
TR3 - Transfer register 3
BR2 - Block register 2 
LLR - Linker list register

This is automatically reconfiguring the GPDMA channel. 
