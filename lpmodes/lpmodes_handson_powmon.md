----!
Presentation
----!
# Power Monitor
## L562 DK Top View
In Low power and LPBAM Hands-on we use Power Shield feature built in L562 Discovery board to for measure purpose and display profile of consumed current in real time.
A small modification of L562 Discovery is needed to be able to measure external power consumption. 

- Keep or switch **SW1 in right position (VDD)** otherwise extra consumption from L562 MCU is add. 

- Select **5V_PM_USB by JP4** as source for L562 board. 

- Connect USB Micro cable to connector below LCD display.

![image1](./img/L5_top.png) 

## L562 DK Bottom view
- Connect **two wires in position 3 & 1 in CN20** as shown in picture below. 

<ainfo>
Wires can be optionally twisted to reduce noise.
</ainfo> 
<p> </p>
![image2](./img/L5_bot.png) 

## Wiring diagram to Nucleo-U575
- **Remove JP5** on Nucleo

- Connect wires to **GND** and **Pin 2** of **JP5**

![image2](./img/wiring.png) 

## Measuring feature of L562 DK
- **Tap on Measurements** icon on LCD 

- No other task is needed for external power measuring

<awarning>
In some cases this step is not needed. Also ignore displayed **Warning** or **Error** message on LCD. This Warning is aplicatable only for consumption measuring of onboard L562 device.
</awarning> 
<p> </p>

## Connect L562-DK board
- [Install](https://www.st.com/en/development-tools/stm32cubemonpwr.html) and launch **STM32CubeMonitor-Power**

- Select **Virtual Comport** associated to L562-DK Power measuring feature.

- Press **Take Control**.

![gif1](./img/CubeMX_PwrMon_SelectBoard.gif)

## Configuration
In Configuration window many parameters can be adjusted. For hands-on purpose let select:

- **Sampling frequency to 100kHz** to get highest resolution

- **Acquisition time set to infinitive** – endless data recording

- **Start Acquisition**.

![gif2](./img/CubeMX_PwrMon_Conf.gif)

