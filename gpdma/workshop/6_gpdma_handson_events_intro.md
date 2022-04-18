----!
Presentation
----!

# Configure events

The events can allow GPDMA to generate interrupts/events or disable this functionality so not interrupt/event wil be created by DMA channel. 

We will set GPDMA only to generte the event/interrupt with last node in list

# Generate event in block transfer

This option is used for our node which is using uart. 

![block event](./img/block_event.json)

# Generate event in last node

This option will be used in our first nodes. Because they are not last. They will **not generate any events**. 

![last lli event](./img/last_lli_event.json)
