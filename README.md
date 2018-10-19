# The Dining Philosophers Problem Project

### Group Number: 5

### Class & Section: CMPE-180C Sec 01 - Operating Systems

### Team Members:

Chanakya Valluri  
Lester Zhang  
Rei Sturm

### Abstract

__Project Overview:__  
Five philosophers are sitting in a round table with a bowl of rice in the center. Each philosopher either thinks or eats. There is a single fork in between each of the philosophers. If a philosopher wants to eat, they grab the forks adjacent to them. Before a philosopher decides to eat, they must ensure both forks are available for use before eating. If both forks are available, the philosophers can eat and puts down the forks when finished and starts thinking again. Otherwise, they must wait until the forks are available.

__Existing approaches and solutions:__  
The resource hierarchy solution involves assigning a partial order to the resources (forks). The resources must be claimed in a certain order. Also, no two resources unrelated by order can be used by a single process (philosopher) simultaneously. If there are 5 forks labelled 1 to 5, each philosopher will always grab the lower-numbered fork first, followed by the higher-numbered fork. The order in which they put down the fork does not matter. As an example, if 4 of 5 philosophers grabbed their respective low-number fork, then only the highest-number fork will remain. The 5th philosopher will not be able to grab a fork. This solution does avoid deadlock. However it is not practical, as the required resources are not known in advance and can become highly inefficient.

The arbitrator solution introduces a waiter in the scene. If a philosopher is hungry, then it must ask the waiter for permission to eat. Permission is only given to one philosopher at a time until that philosopher picks up both forks. The con of this solution is reduced parallelism. If a philosopher is eating and one of the neighbors ask permission to eat, the other philosophers have to wait until that neighbor's request is granted by the waiter even if there are forks still available for the other philosophers.

__Our approach and solutions:__  
We will be implementing a solution where we will use both Pthreads mutex locks and conditional variables. We will make sure that a philosopher will only eat if both forks are available aka picking them up in the critical region. There will be 5 philosophers created and each philosopher will assigned a thread. A function pickup_forks() will be invoked whenever a philosopher wished to eat and philosophers will be alternating between thinking and eating. When the philosopher is finished eating, the forks will be returned using the return_forks() method. Conditional variable are used as a locking mechanism for data integrity with the help of Pthreads mutex locks. The mutex locks will be responsible to allow access to the shared data for the threads.
