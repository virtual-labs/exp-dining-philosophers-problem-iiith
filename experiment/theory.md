## Problem

The dining philosophers problem is invented by E. W. Dijkstra. Imagine that five
philosophers who spend their lives just thinking and easting. In the middle of
the dining room is a circular table with five chairs. The table has a big plate of
spaghetti. However, there are only five chopsticks available, as shown in the
following figure. Each philosopher thinks. When he gets hungry, he sits down and
picks up the two chopsticks that are closest to him. If a philosopher can pick up
both chopsticks, he eats for a while. After a philosopher finishes eating, he puts
down the chopsticks and starts to think.

![dining-philosopher-example](images/DP1.png)

## Analysis

First, we notice that these philosophers are in a thinking-picking up chopsticks-
eating-putting down chopsticks cycle as shown below.

![dining-philosopher-example](images/DP2.png)

The "pick up chopsticks" part is the key point. How does a philosopher pick up
chopsticks? Well, in a program, we simply print out messages such as ``Have left
chopsticks'', which is very easy to do. The problem is each chopstick is shared by
two philosophers and hence a shared resource. We certainly do not want a
philosopher to pick up a chopstick that has already been picked up by his
neighbor. This is a race condition. To address this problem, we may consider
each chopstick as a shared item protected by a mutex lock. Each philosopher,
before he can eat, locks his left chopstick and locks his right chopstick. If the
acquisitions of both locks are successful, this philosopher now owns two locks
(hence two chopsticks), and can eat. After finishes easting, this philosopher
releases both chopsticks, and thinks! This execution flow is shown below.

![dining-philosopher-example](images/DP3.png)

Because we need to lock and unlock a chopstick, each chopstick is associated
with a mutex lock. Since we have five philosophers who think and eat
simultaneously, we need to create five threads, one for each philosopher. Since
each philosopher must have access to the two mutex locks that are associated
with its left and right chopsticks, these mutex locks are global variables.

## Discussion

Key Considerations in Resource Allocation and Deadlock Prevention

* ### Fixed vs. Dynamic Resource Allocation
   * Resources can be pre-assigned to specific entities or allocated
     dynamically.

   * A dynamic approach involves searching for available resources, adding
     realism but increasing complexity.

* ## Order of Resource Acquisition and Release
   * Enforcing a strict sequence for acquiring resources simplifies
     management.

   * The order of releasing resources is often flexible and may not affect
     functionality.

* ## Risk of Deadlock
   * Deadlock occurs when entities lock resources in a circular dependency.
   
   * If every entity acquires a resource and waits for another that is already
     taken, progress halts.

* ## Deadlock Prevention
   * Introduce ordering in resource allocation to avoid circular waiting.

   * Use algorithms like timeouts, priority-based allocation, or breaking the
     cycle dynamically.


![dining-philosopher-example](images/DP4.png)

What if every philosopher sits down about the same time and picks up his left
chopstick as shown in the following figure? In this case, all chopsticks are locked
and none of the philosophers can successfully lock his right chopstick. As a
result, we have a circular waiting (i.e., every philosopher waits for his right
chopstick that is currently being locked by his right neighbor), and hence a
deadlock occurs.

* ## Starvation is also a problem!
   Imagine that two philosophers are fast thinkers and fast eaters. They think
   fast and get hungry fast. Then, they sit down in opposite chairs as shown
   below. Because they are so fast, it is possible that they can lock their
   chopsticks and eat. After finish eating and before their neighbors can lock
   the chopsticks and eat, they come back again and lock the chopsticks and
   eat. In this case, the other three philosophers, even though they have been
   sitting for a long time, they have no chance to eat. This is a starvation. Note
   that it is not a deadlock because there is no circular waiting, and every one
   has a chance to eat!

![dining-philosopher-example](images/DP5.png)

The above shows a simple example of starvation. You can find more complicated
thinking-eating sequence that also generate starvation.