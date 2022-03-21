----!
Presentation
----!


# 1- ICACHE

**The instruction cache tends to reduce the number of accesses to the memory, reducing the overall current consumption**

We have to Initialize Cache in 1-way (direct mapped cache).


<awarning>   
Skipping this step will cause a warning later one. 
</awarning>


![Cubemx start](./img/02.gif)

---

# 2 - LPDMA 

**Two channels will be used respectively for ADC4 sampling and Timer ARR&CNT register updates**

1. Initialize **CH0 **and **CH1** in Linked List Mode
2. **Enable interrupts CH1** in NVIC settings
3. **Keep all default setting** for the other fields

![Cubemx start](./img/03.gif)

---

# 3 -PWR

**SMPS will be enabled here to achieve best power consumption performance even in run mode**

1. Select **SMPS** as Power Regulator from Power Saving tab

<ainfo>
Role of debug pins is detailed in Debug chapter
</ainfo>


![Cubemx pwm](./img/0404.gif)

---

# 4- CLOCK CONFIGURATION 

We can keep default value with MSIS selected and HCLK @4MHz

![Cubemx sys](./img/09.gif)
----
