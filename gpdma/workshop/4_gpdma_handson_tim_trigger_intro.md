
# Use trigger

The ADC+UART are now working in loop. This can be very fast and can also cause a terminal to crash.
But we can slow down the GPDMA by adding trigger.
Then the GPDMA transfer will be conditioned by this trigger event. 

![adc dma uart tim](./img/adc_dma_uart_tim.json)

As trigger source in our case we will use a timer
