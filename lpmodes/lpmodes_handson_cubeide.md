----!
Presentation
----!

# CubeIDE
- Open **CubeIDE** and related LP_mode project

# Flash linker script
In hands-on we disable Flash Bank 2 and disable data retention in almost all SRAMs except 16kB in SRAM4. To avoid any HardFault error or random values founded in variables a correct memory allocation must be defined in *linker script STM32U575ZITX_FLASH.ld*.

- Define RAM memory region only for `SRAM4`
- Also reduce ROM region only to `Flash Bank 1`.

```c
MEMORY
{
  RAM	(xrw)	: ORIGIN = 0x28000000,	LENGTH = 16K
  FLASH	(rx)	: ORIGIN = 0x08000000,	LENGTH = 1024K
}
```
<p> </p>
**Note** in standard application with wider use of power modes and peripheral you might need to place buffers and DMA handlers in dedicated SRAM4 section by using `attribute` 

e.g. `uint32_t variable __attribute__((section(".sram4")));`

# Vcore range
<awarning>
This step is done by CubeMX generator. Proper Vcore level is set dependetly on System clock.
</awarning>
<p> </p>
Use adequate voltage scaling vs. System clock frequency. Vcore Range 4 replaces STM32L4/L5 Low-power run mode. (<24MHz)

- Enable `Vcore Range 4` in `SystemClock_Config()` function.

```c
HAL_PWREx_ControlVoltageScaling(PWR_REGULATOR_VOLTAGE_SCALE4);
```

# All Steps done in combo
- **SMPS Vcore supply**

- **Power Down Flash Bank 2**

To be able observe impact of each further steps let put mcu in Stop 2 mode

- **RTC Autonomous mode**
    Enable the Autonomous Mode for the RTC Stop0/1/2. RTC is part of Smart Run Domain and dedicated clock enable bit must be set otherwise RTC would not wakeup device from STOP modes. 

- **Enter Stop2 mode**

- **SRAMs retention**
    Disable RAM page(s) and caches retention. A content is lost in Stop mode (Stop 0, 1, 2, 3). 

Copy paste following snippet in `USER CODE BEGIN 2 ` section:

```c
  
  /* 1 - Measure consumption in Run LDO operation*/
  HAL_Delay(2000);

  /* 2 - Measure consumption in Run SMPS operation */
  /* The SMPS regulator supplies the Vcore Power Domains */
  HAL_PWREx_ConfigSupply(PWR_SMPS_SUPPLY);
  HAL_Delay(2000);

  /* 3 - Measure consumption for Power-down Mode for Flash Banks */
  /* Enable the Power-down Mode for Flash Banks*/
  HAL_FLASHEx_EnablePowerDown(FLASH_BANK_2);
  HAL_Delay(2000);

  /* Enable ultra low power mode */
  HAL_PWREx_EnableUltraLowPowerMode();

  /* Enable the Autonomous Mode for the RTC Stop0/1/2 */
  __HAL_RCC_RTCAPB_CLKAM_ENABLE();

  /* Set RTC wakeup timer for 2s */
  HAL_RTCEx_SetWakeUpTimer_IT(&hrtc, 2, RTC_WAKEUPCLOCK_CK_SPRE_16BITS, 0);

  /* 4 - Measure consumption in Stop 2 mode Full SRAM retention */
  /* Enter in Stop 2 mode */
  HAL_PWREx_EnterSTOP2Mode(PWR_STOPENTRY_WFI);

  /* Disable RAM page(s) content lost in Stop mode (Stop 0, 1, 2, 3) */
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_SRAM1_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_SRAM2_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_SRAM3_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_ICACHE_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_DCACHE1_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_DMA2DRAM_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_PERIPHRAM_FULL_STOP_RETENTION);
   HAL_PWREx_DisableRAMsContentStopRetention(PWR_PKA32RAM_FULL_STOP_RETENTION);
```
# Periodical wake up from Stop2 mode
- Add Systick delay 2s to be able to measure consumption difference by A-meter

- Set `RTC WakeUp timer` for 2s

- Enter `Stop2 mode`

Copy paste following snippet in `While(1)` user section. 

```c
    /* Led Toggling */
    HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_7);
    HAL_Delay(2000);
    HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_7);

    /* Set RTC wakeup timer for 2s */
    HAL_RTCEx_SetWakeUpTimer_IT(&hrtc, 2, RTC_WAKEUPCLOCK_CK_SPRE_16BITS, 0);

    /* 5 - Measure consumption in Stop 2 mode reduced SRAM retention*/
    /* Enter in Stop 2 mode */
    HAL_PWREx_EnterSTOP2Mode(PWR_STOPENTRY_WFI);
```


  