# ESE 370 Project 2

## Design Problem:
Design a synchronous FIFO that can both enqueue and dequeue an item on each cycle.
- Target technology is the High Performance 22nm process (/home1/e/ese370/ptm/22nm HP.pm)
- Design should be synchronous, with dequeue operations returning a value (if there is
one) on the following cycle.
- We will concretely focus on a FIFO with a maximum capacity of 16, holding 16b-wide data elements.
- Inputs: Clock, In<15:0>, Enqueue, Dequeue
- Outputs: Out<15:0>, Full, Empty
- Full and Empty represent the state of the FIFO at the end of a cycle.
- Dequeue requests are ignored on cycles when Empty is asserted.
- Enqueue requests are ignored on cycles when Full is asserted.
- As a result, simultaneous Enqueue and Dequeue on a cycle when Empty is asserted
will result in no output and a FIFO with one value (the enqueued one), and (b) simultaneous Enqueue and Dequeue on a cycle when Full is asserted will result in no enqueue and a FIFO with one fewer item than its full capacity.
- Nonetheless, if a value is enqueue into an empty FIFO on one cycle, it should be possible to dequeue it on the following cycle.

## Design Metrics:
- area: Sum the total transistor width for the entire design.
- memory cell area: Sum the total transistor width for the repeated memory cell in the
memory core.
- enqueue energy: Measure the energy enqueuing 0xFFFF into a cell that previously
held 0x0000 (and vice-versa). Report the larger value.
- dequeue energy: Measure the energy for a dequeue of a word with 0x0000 and a read
of a word with 0xFFFF. Report the larger value.
- enqueue/dequeue energy: Measure the energy for a cycle that both enqueues and de-
queues values. For test case data, use worst-case scenarios as identified for isolated
enqueue and dequeue.
- standby energy: Measure the energy of a cycle on which no enqueues or dequeues occur.
- average energy: Measure the average energy of your queue with the following opera-
tion distribution: 15% enqueue&dequeue, 10% enqueue, 10% dequeue, 65% standby operation.

## Design:
Your primary objective is energy minimization at 500MHz operation. Your sec- ondary objective is area minimization.
- Vdd ≤ 1.0V.
- A design that only uses complete registers or latches is not acceptable.
- Memory cells should be static.
- You select decoder design, driver design, output sensing/buffer, clocking, control tim-
ing.
- You may not use resistors in the design.
- You get no additional credit for operating faster than 500 MHz.
- You should be trying to minimize all energy components, so the design will be low
energy regardless of the mix of operations. Nonetheless, if you need a concrete distri- bution of operations to help make some decisions, consider: 15% enqueue&dequeue, 10% enqueue, 10% dequeue, 65% no operation.
