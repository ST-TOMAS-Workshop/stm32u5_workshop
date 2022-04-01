# Conclusion

We created pretty complex applicatiuon where

1. We use TIM15 to start GPDMA opperation
2. GPDMA then read data from ADC1 and store them to data array
3. Sort data buffer to data2 with 2d addresing feature
4. Sent data2 over UART
5. Generate IRQ when all data are sent

![complete application](./img/complete_application.json)