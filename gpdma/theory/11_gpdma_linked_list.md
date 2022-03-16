# Linked list

## How is created in code

1. Forst we create configuration structure
2. Then structure is coverted to node confugration (content for registers)

![create node](./img/build_node.json)

3. Then we add this node to queue which we want GPDMA to execute

![add node to queue](./img/insert_node.json)

4. We ling GPDMA to our queue 

![ling queue](./img/link_queue.json)

## Create loops

We can also create loop (circle) in our queue

![circular queue](./img/set_circular.json)

But also only part of the queue can be in loop (circle)

![loop queue](./img/node_loops.json)