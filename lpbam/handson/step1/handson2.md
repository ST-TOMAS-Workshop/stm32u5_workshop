# **Cube MX Peripherals Configuration**

## Steps to initialize the peripherals

**NOTE** 

## 0. **Put in reset state LED RED and LED GREEN,UCPD_DBn and UCPD_FLT from Pinout View**
This will help us to keep lowest power consumption
We will only use Blue LED to know the power state of MCU

![Cubemx start](./img/0101.gif)

---

## 1. **ICACHE**

*Enabled to optimize power consumption. The instruction cache tends to reduce the number of accesses to the memory thus reducing the overall current
consumption*

 First thing we need to do is to Initialize Cache in 1-way (direct mapped cache).

<awarning>   
Skipping this step will cause a warning later one. 
</awarning>


![Cubemx start](./img/02.gif)

---

## 2. **LPDMA**
<!-- check if this can be performed in LPBAM scenario config tab !-->
**Two channels will be used respectively for ADC4 sampling and Timer ARR register update**

1. Initialize CH0 and CH1 in Linked List Mode
2. Enable interrupts CH1 in NVIC settings
3. Keep all default setting for the other fields

![Cubemx start](./img/03.gif)

---

## 3. **PWR**

*SMPS will be enabled here to achieve best power consumption performance even in run mode. Smart Run Domain Debug pins will also be selected*

1. From Debug Pins tab flag select the three options note that PA5,PA6,PA7 appears in GPIO Settings tab 
2. Select SMPS as Power Regulator from Power Saving tab

<ainfo>
Role of PA5,PA6,PA7 will be understood later in this session
</ainfo>


![Cubemx pwm](./img/04.gif)

---

## 4. **SYS**

  *We will use Systick as system timer*

1. Modify default Timebase Source from TIM17 to Systick

Note: This is not absolutely mandatory but goood practice

![Cubemx sys](./img/05.gif)

---

## 5. **USART**

  *Usart will be used to display ADC data buffer values*

1. Click on USART1
2. Mode=Asyncronous
3. Check that by default GPIOs are PA9,PA10 

![Cubemx sys](./img/0202.gif)

---

## 6. **Debug**

  *Set SWD debug pins*

Add SWD debug port from debug tab to avoid need for uncommenting GPIO_Init every time we need to go in low power.

Selected pins by default are PA13, PA14 mapped on STLINK



![Cubemx sys](./img/0303.gif)

## 7. **Clock Configuration**

We can keep default value with MSIS selected and HCLK @4MHz

----
