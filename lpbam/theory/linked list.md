# Linked list #

A channel can be programmed by a list of transfers, known as a list of linked-list items (LLI)

## With Linked list you van decouple configuration of tranfer from their execution ##

- Each Linked-list element item ahs its own data structure
- The base address in memory of the data structure of next linked list item of a channel is the sum of static base address + link address offset


# Autonomous LPDMA #
DMA manages its own clock gating; requesting its clock from the RCC Only when needed in any power mode

LPBAM subsystem can generate asynchronous events / interrupts that can be used to:
- notify the system at the end of a subprocess or of the whole process (for example chaining another task),
-notify the system when a functional error occurred while an LPBAM task was running.


# Autonomous LPDMA #



![theory1](./img/02.png)
![theory1](./img/03.png)
![theory1](./img/04.png)