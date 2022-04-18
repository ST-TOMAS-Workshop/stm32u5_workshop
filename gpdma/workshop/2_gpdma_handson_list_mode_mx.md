----!
Presentation
----!

# Return back to CubeMX

In MX the ADC configuration will be the same 

# Change GPDMA mode

1. Change **GPDMA** mode from `Standard Request Mode` to `Linked-List Mode`

![set list mode](./img/22_03_08_103.png)

# Configure CH15 1/2

1. Got to **CH15** Configuration

![set list mode](./img/22_03_08_105.png)

# Configure CH15 2/2

2. Set **Execution Mode of Linked List** to `Circular`

![set circular mode](./img/22_03_08_107.png)

# Linked List configuration 1/2

1. Go to `LINKEDLIST` periphery in **Utilities**

![LINKEDLIST periphery](./img/22_03_08_109.gif)

# Linked List configuration 2/2

2. Add List by click on `Add List` button

![Add list](./img/22_03_08_111.png)

# Configue List/Queue 1/3

1. Click on Queue to be able configure it. Default name is `YourQueueName`

![select queue](./img/22_03_08_113.png)

# Configue List/Queue 2/3

2. Set **Linear or cicrular LinkedList setting** to `Circular`

![select circular mode](./img/22_03_08_115.png)

# Configue List/Queue 3/3

3. Set first node in loop in our case put `YourNodeName`

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


# Set node parameters same as in previous configuration 1/4

1. In **Request configuration ** set **Request as a patameter** to `GPDMA_REQUEST_ADC1`
   
![request](./img/22_03_08_121.gif)

# Set node parameters same as in previous configuration 2/4

2. In **Destination Data Setting** set **Destination Address Increment After transfer** to `Enabled`

3. In **Destination Data Setting** set **Data Width** to `Half Word`

![destination configuration](./img/22_03_08_123.gif)

# Set node parameters same as in previous configuration 3/4

4. In **Source Data Setting** set **Data Width** to `Half Word`

![source configuration](./img/22_03_08_129.gif)

# Set node parameters same as in previous configuration 4/4

5. In **Runtime configuration** set **Source Address** to `ADC1->DR`

```c
(uint32_t)&(ADC1->DR)
```

6. In **Runtime configuration** set **Destination Address** to `data`

```c
data
```

7. In **Runtime configuration** set **Data Size** to `SIZE`

```c
(64*2)
```

![Runtime configuration](./img/22_03_08_127.png)

# Generate code

Now generate code and switch to CubeIDE