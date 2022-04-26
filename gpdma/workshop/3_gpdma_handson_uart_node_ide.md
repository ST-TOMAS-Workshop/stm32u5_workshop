----!
Presentation
----!

# Start UART 1/2

## 1. First enable DMA request on USART1

By using  `ATOMIC_SET_BIT` into `main.c`

Use 

```c
    ATOMIC_SET_BIT(huart1.Instance->CR3, USART_CR3_DMAT);
```

like 


```c-nc
  /* USER CODE BEGIN 2 */
  MX_YourQueueName_Config();
  HAL_DMAEx_List_LinkQ(&handle_GPDMA1_Channel15, &YourQueueName);

  HAL_DMAEx_List_Start(&handle_GPDMA1_Channel15);
  
  ATOMIC_SET_BIT(huart1.Instance->CR3, USART_CR3_DMAT);

  HAL_ADC_Start(&hadc1);
  /* USER CODE END 2 */
```

# Start UART 2/2

## 2. Start UART for TX

We use `__HAL_UART_ENABLE` to start USART1

Put code

```c
    __HAL_UART_ENABLE(&huart1);
```

like 

```c-nc
  /* USER CODE BEGIN 2 */
  MX_YourQueueName_Config();
  HAL_DMAEx_List_LinkQ(&handle_GPDMA1_Channel15, &YourQueueName);
  HAL_DMAEx_List_Start(&handle_GPDMA1_Channel15);
  
  ATOMIC_SET_BIT(huart1.Instance->CR3, USART_CR3_DMAT);
  __HAL_UART_ENABLE(&huart1);
  
  HAL_ADC_Start(&hadc1);
  /* USER CODE END 2 */
```

# Correct bug in generate by MX

<aerror>
There is an bug in linked_list generation for more nodes
</aerror>

In file `linked_list.c`

Change the YourNodeName2 to YourNodeName around lines 86 and 89.

Cahnge from

```c-nc-line86
  ret |= HAL_DMAEx_List_BuildNode(&pNodeConfig, &YourNodeName2);

  /* Insert YourNodeName2 to Queue */
  ret |= HAL_DMAEx_List_InsertNode_Tail(&YourQueueName, &YourNodeName2);
```

to

```c-line86
  ret |= HAL_DMAEx_List_BuildNode(&pNodeConfig, &YourNodeName);

  /* Insert YourNodeName2 to Queue */
  ret |= HAL_DMAEx_List_InsertNode_Tail(&YourQueueName, &YourNodeName);
```


# What we have

We added uart and use GPDMA to aquire data from ADC and send them over UART

![adc dma uart](./img/adc_dma_uart.json)
