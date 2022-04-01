----!
Presentation
----!

# GPDMA handson adding features

## Current state

* ADC convert samples
* ADC generate request for GPDMA
* GPDMA transfer data to memory

## Next Step

* Now we do the same but with **LLI list**.
* Which allow us later add more lists in later steps

# Classic DMA circular mode

Classical DMA had bit which allow repeat the configuration.
When DMA finished it automatically reload previous configuration.

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

# The GPDMA will use nodes for those reghisters: 

TR1 - Transfer register 1
TR2 - Transfer register 2
BR1 - blck register 1
SAR - Source address register 
DAR - Destination address register
TR3 - Transfer register 3
BR2 - Block register 2 
LLR - Linker list register
