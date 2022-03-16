# Transfer events

The GPDMA can create HT & TC events based on list config

## Block event generation

HT & TC events generated in each block.

![block event](./9_gpdma_transfer_events.mdimg/block_event.json)

## Repeated block generation

HT & TC events generated in the middle of repeated block count and at the end of repeated block.

![repeated block event](./img/burst_block_repblock.json)

## LLI event generation

HT & TC events generated in lli last block configuration

![lli event](./img/lli_event.json)

## Last LLI event generation

HT & TC events only generated in last lli and last block configuration. Only if LLI is last

![repeated block event](./img/last_lli_event.json)