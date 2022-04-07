----!
Presentation
----!

# Select linked list

1. Open `LINKEDLIST`
2. Select `YourNodeName` node
3. In **Transfer Event Generation** section set **Transfer Event Generation** to `The TC event is generate at the end of the last linked-list item`
4. Select `YourNodeName3` node
5. In **Transfer Event Generation** section set **Transfer Event Generation** to `The TC event is generate at the end of the last linked-list item`
6. Select `YourNodeName2` node
7. In **Transfer Event Generation** section set **Transfer Event Generation** to `The TC event is generate at the end of each block`

![set event](./img/22_03_14_187.gif)

Because we are in loop the `end of the last linked-list item` condition is newer met so node willl not generate any event/interrupt. 
Only `YourNodeName2` will generate event/interrupt for each block. We have only one block so one interrupt

# Generate code

1. Click on **Generate Code**
2. Go to **CubeIDE**
