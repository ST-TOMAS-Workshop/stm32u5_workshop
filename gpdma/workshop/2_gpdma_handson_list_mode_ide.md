----!
Presentation
----!

# Add linked_list.h include

First add **include** of `linked_list.h` into `main.c`

By adding 

```c
#include "linked_list.h"
```

To `USER CODE BEGIN Includes` section

```c-nc
/* USER CODE BEGIN Includes */
#include "linked_list.h"
/* USER CODE END Includes */
```

# Create buffer where to store ADC values

We create array `data` of 16bit elements with size 64 elements

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

# Add Queue handle to main

Add `YourQueueName` extern variable to our `main.c`

By adding 

```c
extern DMA_QListTypeDef YourQueueName;
```

like 

```c-nc
/* USER CODE BEGIN PV */
uint16_t data[64];

extern DMA_QListTypeDef YourQueueName;
/* USER CODE END PV */
```

# Add size and data also to Queue config

Add 

```c
extern uint16_t data[];
```

to `linked_list.c` section `/* USER CODE BEGIN PM */` like

```c-nc
/* USER CODE BEGIN PM */
extern uint16_t data[];
/* USER CODE END PM */
```

# Call queue config

Use `MX_YourQueueName_Config` to initialize our nodes and queue.

Add

```c
  MX_YourQueueName_Config();
```

to `/* USER CODE BEGIN 2 */` section in `main.c` like


```c-nc
  /* USER CODE BEGIN 2 */
  MX_YourQueueName_Config();
  /* USER CODE END 2 */
```