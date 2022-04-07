----!
Presentation
----!

# Use 2D addressing

Now we exten our example even more. 

In current setup the channels from adc are stored in buffer like 
CH1_a, CH2_a, CH3_a, CH4_a, CH1_b, CH2_b, CH3_b, CH4_b
but we would like organization like 
CH1_a, CH1_b, CH2_a, CH2_b, CH3_a, CH3_b, CH4_a, CH4_b

For this we will use 2D addressing feature of GPDMA

# How the 2D addresing can looks like

![2d addresing](./img/2d_addresing_offsets.json)

# How it will work for us

![2d addresing in our app](./img/2d_addresing.json)
