# Benchmark

We now need to compare low power result vs standard approach. 

Here below you can see the example of an application which is performing same task without LPBAM.

ADC is set at 1.5Clk cycles sampling and 4MHz MSIK.
LPTIM is still changing frequency between 256Hz and 64Hz and it is powered by LSI

---

<ainfo>
Of course there are many more possible scenario to achieve same result, this is only first example.

We will extend the applicabilty of our findings in next chaper on results discussion.
</ainfo>

---

# Standard application w/o LPBAM


![Cubemx start](./img/0700.png)


## Cube IDE Project Build

Open the project included in webinar folder pack.
Build and program it into NUCLEO-U575ZIQ

![Cubemx start](./img/0701.png)

## Power Measurement

Follow the steps showed in the previous chapter

1 -Connect STM32L562E-DK 

2- Open `STM32 Cube Monitor Power`

3- Start the measurement

![Cubemx start](./img/0702.png)

## Sampling frequency change
We are going to test how this power consumption value changes when sampling frequency increases by a factor 10x

in 'private define' section add

```c
#define FREQUENCY_TEST

```
Build and Run the application then connect Power Monitor and start measurement

![Cubemx start](./img/0703.png)


<ainfo>
We now move to result discussion in order to compare LPBAM vs interrupt based approach
</ainfo>