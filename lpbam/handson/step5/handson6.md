# Powe Measurement

We will now measure power consumption using STM32L562E-DK and STM32 Cube Monitor Power

Please follow the below steps

## Board Switch and jumper config
![lpbam config](./img/0501.png)

## Board connection to Nucleo-U575ZIQ

![lpbam config](./img/0502.png)

## STM32CubeMonitor-Power settings

![lpbam config](./img/0503.png)

## Power measurement

<awarning>
If Nucleo-U575 is no more connected and does not reset, reconnect jumper to JP5 and run a new power cycle
</awarning>

![lpbam config](./img/0504.png)

## Power sequence

![lpbam config](./img/0505.png)


## LPBAM Power consumption result

![lpbam config](./img/0506.png)

<ainfo>
This power consumption is already remarkable but can be firtherly optimized by disabling UART, PWR debug pins setting as Analog mode
</ainfo>


## Test with slower MSIK