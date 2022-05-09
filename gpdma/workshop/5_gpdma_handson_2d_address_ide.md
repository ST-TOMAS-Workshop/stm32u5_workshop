----!
Presentation
----!

# Add new buffer

In `main.c`
Add new buffer to section `/* USER CODE BEGIN PV */`

```c
uint16_t data2[64];
```


```c-nc
/* USER CODE BEGIN PV */
uint16_t data[64];
uint16_t data2[64];

extern DMA_QListTypeDef YourQueueName;
/* USER CODE END PV */
```

# Add buffer to linked_list.c

To file `linked_list.c`
To section `/* USER CODE BEGIN PM */` add

```c
extern uint16_t data2[];
```

like 

```c-nc
/* USER CODE BEGIN PM */
extern uint16_t data[];
extern uint16_t data2[];
/* USER CODE END PM */
```

# Node correction because of MX

<aerror>
Mx contains an bug.

There is a missing configuration for YourNodeName2.
</aerror>

To file `linked_list.c` add
 
```c
  pNodeConfig.RepeatBlockConfig.RepeatCount = 1;
  pNodeConfig.RepeatBlockConfig.SrcAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.DestAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.BlkSrcAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.BlkDestAddrOffset = 0;
```

like

```c-nc
  /* Set node configuration ################################################*/
  pNodeConfig.Init.Request = GPDMA1_REQUEST_USART1_TX;
  pNodeConfig.Init.Direction = DMA_MEMORY_TO_PERIPH;
  pNodeConfig.Init.DestInc = DMA_DINC_FIXED;
  pNodeConfig.Init.SrcDataWidth = DMA_SRC_DATAWIDTH_BYTE;
  pNodeConfig.Init.DestDataWidth = DMA_DEST_DATAWIDTH_BYTE;
  pNodeConfig.Init.TransferEventMode = DMA_TCEM_BLOCK_TRANSFER;
  pNodeConfig.RepeatBlockConfig.RepeatCount = 1;
  pNodeConfig.RepeatBlockConfig.SrcAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.DestAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.BlkSrcAddrOffset = 0;
  pNodeConfig.RepeatBlockConfig.BlkDestAddrOffset = 0;
  pNodeConfig.SrcAddress = data2;
  pNodeConfig.DstAddress = &(USART1->TDR);
  pNodeConfig.DataSize = (64*2);
  ```

# Now compile and run application

Compile code and run debug we can check content of `data` and `data2`

# What we created

We added new node which can sort the content before is sent over by UART

![2d addresing](./img/2d_addresing.json)
