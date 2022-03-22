----!
Presentation
----!

# 1. GPDMA + ADC

 We create simple example where first GPDMA transfersdata from ADC. 

![adc dma description](./img/adc_dma_desc.json)

# Create new project

1. Start new project. For STM32U575ZIT
   Description can be found on this [Link](./../utility_config/mx_create_project.md)

# Select ADC1 periphery

Select `ADC1` in **Analog**

![select ADC](./img/22_01_28_57.gif)

# Enable 4 adc channels
Enable channels IN1 to IN4

![select 4 channels](./img/22_01_28_59.gif)

# Configure the ADC 1/4

1. Set `Continuous conversion mode` to **Enable**

This optiion run ADC in loops. When ADC finish converting all its channesl it will start again from beginning.

2. Set `Low power wait` to **Enable**

This option will stop ADC until the DATA are read form it. It is good to prevent overrun. And we are sure that we have still correct order of channels.

3. Set `Enable Regular Conversions` to **Enable**

![configure adc 1](./img/22_01_28_61.gif)

# Configure ADC 2/4

1. Set `Conversion Data Management Mode` to **DMA Circular Mode**

After ADC convert value it will create request for DMA. Curcular mode here means that after ADC finish all regular channels it will continue generate DMA request in next run too.

![configure adc 2](./img/22_01_28_81.png)
# Configure the ADC 3/4

1. Set `number of conversion` to **4**

This will set ADC to do 4 ADC conversion which we can set.

![configure adc 3](./img/22_01_28_69.gif)
# Configure the ADC 4/4

1. You can set ADC channel for each `Rank`

Each rank will have assing one ADC channel to convert. It is possible to select same chanel each time.

![configure adc 4](./img/22_01_28_65.gif)

# Select GPDMA1

1. Sececd `GPDMA1` in **System Core**
2. Enable channel with 2D addressing (12-15)

![Enable GPDMA](./img/22_01_28_71.gif)

# Configure GPDMA1 CH15 1/2

1. Select CH15(or channel which you selected CH12-CH15)
2. Set `Circular Mode` to **Enable**
3. Set `Request` to **ADC1**

![configure GPDMA ch15 1](./img/22_01_28_79.gif)

# Configure GPDMA1 CH15 2/2

1. Set `Source Data Settings` - `Data Width` to **Half Word**
2. Set `Destination Data Settings` - `Data Width` to **Half Word**
3. Set `Destination Data Settings` - `Destination Address Increment After Transfer` to **Enable**

![configure GPDMA ch15 2](./img/22_01_28_77.gif)

# Set project name and Generate project and Import to CubeIDE

1. How to generate project is described here [Link](./../utility_config/mx_generate_code.md)
2. Import project to CubeIDE [Link](./../utility_config/ide_import_project.md)

<ainfo>
When used CubeIDE instead of CubeMX to create project no import is needed
</ainfo>

# Create buffer where to store ADC values

We create array `data` of 16bit elements wuth size as `SIZE`which is 64 elements

Like this

```c
uint16_t data[64];
```

Put the array and size into `main.c` to section ` USER CODE BEGIN PV` like bellow

```c-nc
/* USER CODE BEGIN PV */
uint16_t data[64];
/* USER CODE END PV */
```

# Enable VDDA

To save more power the VDDA is disabled on U5 by default. 
We must enable it by adding 

```c
  __HAL_RCC_PWR_CLK_ENABLE();
  HAL_PWREx_EnableVddA();
```

to `/* USER CODE BEGIN SysInit */` section in `main.c`

```c-nc
  /* USER CODE BEGIN SysInit */
  __HAL_RCC_PWR_CLK_ENABLE();
  HAL_PWREx_EnableVddA();
  /* USER CODE END SysInit */
```

# Start ADC and DMA

To start ADC+DMA we can use HAL function `HAL_ADC_Start_DMA`
We use it like this:

```c
  HAL_ADC_Start_DMA(&hadc1, data, 64);
```

we put it into section `USER CODE BEGIN 2` like bellow

```c-nc
  /* USER CODE BEGIN 2 */
  HAL_ADC_Start_DMA(&hadc1, data, 64);
  /* USER CODE END 2 */
```

`&hadc1` - is ADC handle which contains information about ADC1 and related DMA channel

`data` - buffer where to store data from ADC
`SIZE` - `data` buffer size 

# Compile code and run debug

1. Run debug [Link](./../utility_config/ide_debug.md)

# In debug open Live Expression

Live expression showing changes in watched variables

![Open Live expression](./img/22_02_03_83.gif)

# Add variable to live watch

![Add to live watch](./img/22_02_03_85.gif)

# Run code and check changing content

Fun code by pressing `F8` or press Run 

![Run code](./img/22_02_03_89.gif)

# What we created

![adc dma description](./img/adc_dma_desc.json)



