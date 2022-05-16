----!
Presentation
----!

# Select ADC1 peripheral

Select `ADC1` in **Analog**

![select ADC](./img/22_01_28_57.gif)

# Enable 4 adc channels
Enable channels IN1 to IN4

![select 4 channels](./img/22_01_28_59.gif)

# Configure the ADC 1/4

1. Set `Continuous conversion mode` to **Enable**

This option run ADC in loops. When ADC finish converting all its channels it will start again from beginning.

2. Set `Low power wait` to **Enable**

This option will stop ADC until the DATA are read from it. It is good to prevent overrun. And we are sure that we have still correct order of channels.

3. Set `Enable Regular Conversions` to **Enable**

![configure adc 1](./img/22_01_28_61.gif)

# Configure ADC 2/4

1. Set `Conversion Data Management Mode` to **DMA Circular Mode**

After ADC converts value, it will create request for DMA. Circular mode here means, that after ADC finishes, all regular channels it will continue to generate DMA request in next run too.

![configure adc 2](./img/22_01_28_81.png)
# Configure the ADC 3/4

1. Set `number of conversion` to **4**

This will set ADC to do 4 ADC conversions which we can set.

![configure adc 3](./img/22_01_28_69.gif)
# Configure the ADC 4/4

1. You can set ADC channel for each `Rank`

Each rank will have assigned one ADC channel to convert. It is possible to select same channel each time.

![configure adc 4](./img/22_01_28_65.gif)

# Change GPDMA mode

1. Select **GPDMA1** in **System** category
2. Set mode to `Linked-List Mode`

![set list mode](./img/22_03_08_103.png)

# Configure CH15 1/2

1. Go to **CH15** Configuration

![set list mode](./img/22_03_08_105.png)

# Configure CH15 2/2

2. Set **Execution Mode of Linked List** to `Circular`

![set circular mode](./img/22_03_08_107.png)

# Linked List configuration 1/2

1. Go to `LINKEDLIST` peripheral in **Utilities**

![LINKEDLIST periphery](./img/22_03_08_109.gif)

# Linked List configuration 2/2

2. Add List by clicking on `Add List` button

![Add list](./img/22_03_08_111.png)

# Configue List/Queue 1/3

1. Click on Queue to be able to configure it. Default name is `YourQueueName`

![select queue](./img/22_03_08_113.png)

# Configue List/Queue 2/3

2. Set **Linear or circular LinkedList setting** to `Circular`

![select circular mode](./img/22_03_08_115.png)

# Configue List/Queue 3/3

3. Set first node in loop, in our case put `YourNodeName`

```c
YourNodeName
```

![select first node name](./img/22_03_08_117.png)

# Node loop

The first node in loop is where LLR from last node in queue will be pointed.
You can select any node in queue.
In our case when YourNodeName finishes he will reload same configuration. Because he is pointing on himself.

![node loop](./img/node_loops.json)

# Node configuration

1. Select Node

![select first node name](./img/22_03_08_119.png)


# Set node parameters same as in the previous configuration 1/4

1. In **Request configuration ** set **Request as a parameter** to `GPDMA_REQUEST_ADC1`
   
![request](./img/22_03_08_121.gif)

# Set node parameters same as in the previous configuration 2/4

2. In **Destination Data Setting** set **Destination Address Increment After transfer** to `Enabled`

3. In **Destination Data Setting** set **Data Width** to `Half Word`

![destination configuration](./img/22_03_08_123.gif)

# Set node parameters same as in the previous configuration 3/4

4. In **Source Data Setting** set **Data Width** to `Half Word`

![source configuration](./img/22_03_08_129.gif)

# Set node parameters same as in the previous configuration 4/4

5. In **Runtime configuration** set **Source Address** to `ADC1->DR`

```c
(uint32_t)&(ADC1->DR)
```

6. In **Runtime configuration** set **Destination Address** to `data`

```c
data
```

7. In **Runtime configuration** set **Data Size** to `(64*2)`

```c
(64*2)
```

![Runtime configuration](./img/22_05_16_193.gif)

# Generate code

Now generate code and switch to CubeIDE