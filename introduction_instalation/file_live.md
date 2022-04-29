----!
Presentation
----!

# Introduction
## Dear Participant of STM32U5 Workshop,
<br>

Welcome to this short step-by-step guide which could help you to prepare to live version of STM32U5 Workshop session.

You will find here:

 - all information about prerequisites (software and hardware), 
 - short information about installation process, 
 - links to materials useful for this session

Additionally, in appendixes you can find some basic information about the board we will use durig the session and useful information about configuraiton and usage of STM32CubeIDE built in terminal
<br>

To navigate within this manual, please use navigation buttons:
<br>

  ![navigation](./img/navigation.gif)

<br>

In case of any questions / problems please contact us on [link](https://community.st.com)

See you on STM32U5 Workshop live session
<br>

## Yours, 
## STMicroelectronics 
<br>

# Prerequisites
- Hardware:
  - **PC with MS Windows 10 operating system and admin rights granted**
  - **2 micro USB** cables 
  <br>
  ![microUSB cables](./img/uUSB.jpg)  ![microUSB cables](./img/uUSB.jpg)
  <br>
  - **2 female-female wires** (min 10cm length) to connect gold pins 
  <br>
  ![microUSB cables](./img/Cables.gif)
  <br>
  - **[NUCLEO-U575ZI-Q](https://www.st.com/en/evaluation-tools/nucleo-u575zi-q.html)** board (will be delivered on the session)
  <br>
  ![U5_Nucleo](./img/Nucleo_U5_small.jpg)
  <br>
  - **[STM32L562E-DK](https://www.st.com/en/evaluation-tools/stm32l562e-dk.html)** board which will be lent to each participant for the time of the workshop 
  <br>
  ![L5_DK](./img/STM32L5_DK.jpg)
  <br>
  (alternatively you can take your own multimeter with 1uA current measurement range)
  <br>
  ![Multimeter](./img/Multimeter.jpg)
  <br>
- Software (PC with **MS Windows 10** operating system):
  - **[STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)** in version 6.5.0
  - **[STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)** in version 1.9.0
  - **[STM32U5 Cube library](https://www.st.com/en/embedded-software/stm32cubeu5.html)** in version 1.1.0
  - **[STM32Cube Monitor Power](https://www.st.com/en/development-tools/stm32cubemonpwr.html)** in version 1.1.1
  - **[Virtual COM port drivers](https://www.st.com/en/development-tools/stsw-stm32102.html)**
  - `[optionally]` any **terminal** application (can be used the one from STM32CubeIDE)
<br>



# Installation process
- download **STM32CubeMX** from [here](https://www.st.com/en/development-tools/stm32cubemx.html)
- install **STM32CubeMX** (if not yet done)
- download **STM32CubeIDE** from [here](https://www.st.com/en/development-tools/stm32cubeide.html)
- Install **STM32CubeIDE** (if not yet done)
- download and install **STM32U5 Cube library** (if not done yet):
  - run **STM32CubeIDE**
  - go to `Help -> Manage Embedded Software Packages`
  - within package manager window find `STM32U5`, unroll it and select newest available version
  - press `install now`
<br>
![U5_Lib_Install](./img/U5_Lib_install.gif)
<br>
In case of library installation problems please try an alternative way:
 - download **STM32U5 Cube library** (.zip file)
 - run **STM32CubeIDE**
 - go to `Help -> Manage Embedded Software Packages`
 - within packager manager window use option `From local` 
<br>  
![U5_Lib_Install_from_local](./img/U5_Lib_install_from_local.gif)

<br>

<ainfo>
STM32CubeMX and STM32CubeIDE are using the same repository by default, so installed STM32U5 Cube library will be visible in both tools.
</ainfo>


<br>
- download and install **STM32CubeMonitor-Power** (if not yet done) from [here](https://www.st.com/en/development-tools/stm32cubemonpwr.html):
<br>
In case you would like to know more about this tool and its usage you can have a look at dedicated [video](https://youtu.be/COOi_BiPE5U).

<br>
----

# Verification process
The purpose of this part is checking whether all software components are installed properly.
<br>
Additionally prepared test project can be a base for next hands-on parts during the workshop.

## ** 1 STM32CubeIDE and STM32U5 Cube library**
<br>

----

<br>
## **Task definition**
<br>
- Using STM32CubeIDE:
 - Configure system clock (SYSCLK and HCLK) to 4MHz using internal MSI oscillators (default settings)
 - Configure ICACHE (in any of available modes)
 - Select and configure USART1:
   - in asynchronous mode, 
   - using default settings (115200bps, 8D, 1stop bit, no parity) 
   - on PA9/PA10 pins
<br>

----

<br>
## **Step1** - project creation and peripherals configuration
 - Run **STM32CubeIDE**
 - Specify workspace location (i.e. `C:\_Work\U5_WS`)
<br>
![Workspace_start](./img/New_prj_start.gif)
<br>
- Start new project using one of the below methods:
  - by selecting `File->New->STM32Project` 
  - by click on `Start new STM32 project` button
  <br>
  ![Workspace_start2](./img/New_prj_start_2.gif)
<br>
- select STM32**U575ZI**TxQ MCU (the one present on NUCLEO-U575ZI-Q board)
- press `Next` button
- within STM32 Project window:
  - specify project name (i.e. `U5_Basic`)
  - keep **enable TrustZone** option unchecked
  - press `Finish` button
  - on warning pop-up window press `Yes` button
  <br>
   ![Workspace_start3](./img/New_prj_start_3.gif)
<br>
- within **Clock Configuration** tab:
  - keep the default settings (4MHz based on MSI)
<br>
  ![Clock configuration](./img/Clock_conf.gif)
<br>
- Peripherals configuration: Pinout&Configuration tab
- **ICACHE configuration** (System Core group)
  - select either 1-way or 2-ways (we will not focus on performance within this workshop)
  <br>
  ![ICACHE configuration](./img/ICACHE_conf.gif)
  <br>
- **USART1 configuration** (Connectivity group)
  - select Asynchronous mode
  - keep default settings in configuration:
    - Basic parameters: 115200bps, 8bits data, 1 stop bit, no parity
    - Pins assignment: PA9, PA10
    - no interrupts, no DMA usage
  <br>
    ![USART1 configuration](./img/USART1_conf.gif)
<br>
- **Project settings**
  - select `Project Manager` tab
  - check project location (.ioc file)
  - check project name
<br>
   ![Project settings](./img/Prj_settings.gif)
<br>
  - generate project by one of the ways:
    - by pressing "gear" icon
    - by select `Project->Generate Code`
    - by pressing **Alt+K**
<br>
  ![Project generation](./img/Prj_gen.gif)
<br>
 - In case you see a warning pop-up window concerning SMPS configuration, please OK. This will be explained in next parts of the session.

----

<br>
## **Step2** - coding part (`main.c` file)
<br>
Define the buffer of bytes to be sent over **USART1** (`USER CODE PV` section):
<br>

```c
uint8_t buffer[]={"Homework exercise\n"};
```

<br>
![Coding1](./img/Code_copy1.gif)
<br>
Start transmit of the data over **USART1** using prepared buffer and ***polling*** method (`USER CODE 2` section):
<br>

```c
HAL_UART_Transmit(&huart1, buffer, 18, 200);
```

<br>
![Coding2](./img/Code_copy2.gif)
<br>

----

<br>
## **Step 3** - build the project
- Build the project using `hammer` button or `Project->Built All` or **Ctrl+B**
<br>
![Project build](./img/Build.gif)
<br>

<ainfo>
In case of neither errors nor warnings after this process, STM32CubeIDE and STM32U5 library are installed correctly. Last point - debug session will be verified during first hands on part on the workshop.
</ainfo>

## ** 2 STM32CubeMonitorPower **

Please start STM32CubeMonitorPwr and check that you can see similar window as a final effect.
<br>
![STM32CubeMonitorPwr](./img/CubeMonPwr.gif)
<br>


<ainfo>
## **Congratulations** You have completed installation part. Now you are fully prepared for the live workshop session. 
</ainfo>

----


# **Appendix A** - Board overview
 <br>
**NUCLEO-U575ZI-Q** board
[schematics](https://www.st.com/resource/en/schematic_pack/mb1549-u575ziq-c03_schematic.pdf)
![NUCLEO-U575ZI-Q board](./img/Nucleo_U5_overview.jpg)
<br>

----


<br>

# **Appendix B** - configuration and start **STM32CubeIDE** built-in terminal  
<br>
### You can follow dedicated video on this topic [here from 8:50](https://www.youtube.com/watch?v=JWOV4j5fCS4&list=PLnMKNibPkDnFCosVVv98U5dCulE6T3Iy8&index=11&t=569s)

- Being in the debug session (debug perspective), please go to Console window (bottom part of the screen) 
- select `New -> 3 Command Shell Console` 
- specify `Connection Type` to **Serial Port**
- select **New** within `Connection name` (in case of previously configured connections you can select them from the list)
- in case of new connection, select its name (i.e. `Internal_Term`)
- select port number (used by STLink Virtual COM port - usually highest from the list)
- adapt communication parameters if needed (in our case default settings are inline with application ones)
- to confirm press `Finish`
- press `OK` on the next window
- After proper configuration, Console will contain terminal window (already connected)
- It is possible to disconnect the terminal, connect it or close it
<br>  
  ![Built-in terminal](./img/IDE_terminal.gif)

# Materials for the session
- Access to tools dedicated web pages:
  - [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)
  - [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)
  - [STM32U5 Cube library](https://www.st.com/en/embedded-software/stm32cubeu5.html)
  - [STM32CubeMonitorPower](https://www.st.com/en/development-tools/stm32cubemonpwr.html)
- [STM32 on-line training resources](https://www.st.com/content/st_com/en/support/learning/stm32-education/stm32-moocs.html)
- documentation
  - [STM32U575 datasheet](https://www.st.com/resource/en/datasheet/stm32u575zi.pdf)
  - [STM32U575 reference manual](https://www.st.com/resource/en/reference_manual/rm0456-stm32u575585-armbased-32bit-mcus-stmicroelectronics.pdf)
  - [NUCLEO-U575ZI-Q board schematics](https://www.st.com/resource/en/schematic_pack/mb1549-u575ziq-c03_schematic.pdf)


  Alternatively you can download complete set of offline materials from [this link]()

# Verification process at the begining of the session

  The purpose of this part is checking whether all software components can run with provided hardware boards.
  <br>
  **We will reuse the project prepared within homework part.**

- Please start STM32CubeIDE and open the project prepared before the session.
- Connect board to PC using micro-USB cable. Multicolor LED (right side of USB connector) should be turned on (red color)
<br>
![Board connection](./img/Nucleo_connect.gif)
<br>
- Start the debug session using `bug` icon or `Run->debug` or by pressing **F11**
- All the settings should be automatically set based on your compiled project. Press `OK` button
- At this moment you may see an information window that your STLink firmware is not up-to-date,
- please accept this message and perform automatic upgrade process
<br>
![STLink_upgrade](./img/STLink_upgrade.gif)
<br>
- Select `Switch` within `Configure Perspective Switch` dialog which is informing about new (debug one) windows setup within STM32CubeIDE application.
<br>
![Project debug](./img/start_debug.gif)
<br>
- Start terminal application and run it for virtual COM port number assigned to the NUCLEO board with settings: 115200bps, 8bits data, 1 stop bit, no parity, no HW control. As an alternative you can use STM32CubeIDE built-in terminal (please have a look within Appendix for more details)
- run the application within debug session. As a result within terminal there should be "Homework exercise" message displayed.
  <br>
![Final app](./img/App_run_small.gif)
<br>.

----

<ainfo>
 **Congratulations** You have completed varifictation part. Now you are fully prepared for next parts of this workshop session 
</ainfo>

----

