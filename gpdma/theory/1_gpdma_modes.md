# CubeMX modes

MX offers two modes for GPDMA

## Standard Request Mode

In this mode the GPDMA will be similar to normal DMA frlo older STM32s

### Non circular mode

Same as old DMA. After GPDMA finished the transfer it is disabled

### Circular mode

If cicruclar is used. The MX will create one node loop for us with configuration
When the GPDMA finishes the transfer configuration is reloaded

![circular](./img/gpdma_list.json)

## Linked List Mode

The main configuration here done in **LINKEDLIST** periphery. The GPDMA will execute this created list. 

