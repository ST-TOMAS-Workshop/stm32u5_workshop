----!
Presentation
----!

# What does MX_YourQueueName_Config? 1/3

The fucntion will create our node configuration from structure by using `HAL_DMAEx_List_BuildNode`
The node is now copy of gpdma registers. 
But still no link between nodes. 

![build node](./img/build_node.json)

# What does MX_YourQueueName_Config? 2/3


To link nodes together MX use `HAL_DMAEx_List_InsertNode_Tail`
To create our queue.

![add node](./img/insert_node.json)

# What does MX_YourQueueName_Config? 3/3

To put nodes into circular loo we use `HAL_DMAEx_List_SetCircularMode`

![circular node](./img/set_circular.json)
