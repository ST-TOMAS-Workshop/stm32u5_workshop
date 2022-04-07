# Use D2D addressing

<aerror>
Currenlty under construction
</aerror>

Now we exten our example even more. 

In current setup the channels from adc are stored in buffer like 
CH1_a, CH2_a, CH3_a, CH4_a, CH1_b, CH2_b, CH3_b, CH4_b
but we would like organization like 
CH1_a, CH1_b, CH2_a, CH2_b, CH3_a, CH3_b, CH4_a, CH4_b

For this we will use 2D addressing feature of GPDMA




# Add new buffer

Add new buffer to section `/* USER CODE BEGIN PV */`

```c
uint16_t data2[SIZE];
```


```c-nc
/* USER CODE BEGIN PV */
#define SIZE 64
uint16_t data[SIZE];
uint16_t data2[SIZE];

extern DMA_QListTypeDef YourQueueName;
/* USER CODE END PV */
```

# Add buffer to linked_lic

To file `linked_list.c`
To section `/* USER CODE BEGIN PM */` add

```c
extern uint16_t data2[];
```

like 

/* USER CODE BEGIN PM */
#define SIZE 64
extern uint16_t data[];
extern uint16_t data2[];
/* USER CODE END PM */

# Node correction because of MX

<aerror>
Mx contains an bug 
He will not generate half word configuration for us 
</aerror>

To file `linked_list.c` add
 
```c
  pNodeConfig.Init.SrcInc = DMA_SINC_INCREMENTED;
  pNodeConfig.Init.DestInc = DMA_DINC_INCREMENTED;
```

like

```c-nc
  /* Set node configuration ################################################*/
  pNodeConfig.Init.Request = DMA_REQUEST_SW;
  pNodeConfig.Init.Direction = DMA_MEMORY_TO_MEMORY;
  pNodeConfig.Init.SrcBurstLength = 2;
  pNodeConfig.Init.DestBurstLength = 2;
  pNodeConfig.Init.SrcInc = DMA_SINC_INCREMENTED;
  pNodeConfig.Init.DestInc = DMA_DINC_INCREMENTED;
  pNodeConfig.RepeatBlockConfig.RepeatCount = 16;
  pNodeConfig.RepeatBlockConfig.DestAddrOffset = 30;
  pNodeConfig.RepeatBlockConfig.BlkDestAddrOffset = -126;
  pNodeConfig.SrcAddress = data;
  pNodeConfig.DstAddress = data2;
  pNodeConfig.DataSize = 8;
  ```

  