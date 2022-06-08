----!
Presentation
----!

# MX get rid of the pop-up message

This part is optional. It's not affecting the GPDMA. The purpose is to remove the pop-up message about SMPS and I-Cache for each code generation.

![popup message](./img/2022-05-16-11_05_19.png)

# Enable I-Cache

1. Select **ICache** periphery
2. Set Mode 1-way (direct mapped cache)

This enable the I-Cache which is used instead of Flash so code exacution is faster(This is not important for our GPDMA handson)

![Enable Icache](./img/22_05_16_199.gif)

# Enable SMPS

1. select **PWR** periphery
2. Set **Power regulator** to `SMPS`

![Enable SMPS](./img/22_05_16_201.gif)

The SMPS is more effective power supply than LDO. With SMPS is possible reach lower power consumption. 
Disadvantage is that SMPS need external components. And SMPS is making bigger electrical noise then LDO. 

