----!
Presentation
----!

# Connect queue and GPDMA channel

To connect Queue and GPDMA we will use `HAL_DMAEx_List_LinkQ`

Add

```c
HAL_DMAEx_List_LinkQ(&handle_GPDMA1_Channel15, &YourQueueName);
```

to section `/* USER CODE BEGIN 2 */` like

```c-nc
  /* USER CODE BEGIN 2 */
  MX_YourQueueName_Config();
  
  HAL_DMAEx_List_LinkQ(&handle_GPDMA1_Channel15, &YourQueueName);
  /* USER CODE END 2 */
```

First parameter `handle_GPDMA1_Channel15` is GPDMA handle
Second parameter `YourQueueName` is our Queue

# Start GDMA and ADC

Start DMA by using `HAL_DMAEx_List_Start`
ADC is started by using `HAL_ADC_Start`

Add 

```c
  HAL_DMAEx_List_Start(&handle_GPDMA1_Channel15);
  HAL_ADC_Start(&hadc1);
```

To section `/* USER CODE BEGIN 2 */` like 

```c-nc
  /* USER CODE BEGIN 2 */
  MX_YourQueueName_Config();

  HAL_DMAEx_List_LinkQ(&handle_GPDMA1_Channel15, &YourQueueName);

  HAL_DMAEx_List_Start(&handle_GPDMA1_Channel15);
  HAL_ADC_Start(&hadc1);
  /* USER CODE END 2 */
```

## Compile code and run debug

# What we created

We have similar application like in Basic GPDMA. But now based directly on linked list, where we can add more elements


# Add link to GPDMA

We lined node to our GPDMA channel with `HAL_DMAEx_List_LinkQ`

![link queue](./img/link_queue.json)
