# Dining Philosopher's Problem

The Dining Philosophers Problem is a classic problem in computer science that explores the ways in which 
concurrent processes (or threads) can deadlock. 
The problem is often used as a metaphor for the challenges of managing and coordinating multiple processes that share resources.

In this implementation, the problem is solved using the pthreads library in C, which provides tools
for creating and managing concurrent threads. The code defines five "philosophers" who are represented by threads,
and each philosopher has access to two "forks" that they can pick up and use to eat. 
The problem is that if all five philosophers try to pick up their left fork at the same time, 
they will all be blocked and unable to eat, leading to a deadlock.

To prevent this from happening, the code uses a mutex (a kind of lock) to coordinate access to the forks. 
Before a philosopher can pick up their forks, they must first acquire the mutex lock. 
This ensures that only one philosopher can pick up their forks at a time. 
The code also uses conditional variables (or "conds") to allow philosophers to block until they are able to pick up their forks. 
This means that if a philosopher tries to pick up their forks and they are unavailable, 
the philosopher will be blocked until the forks are put down by another philosopher.

The code consists of several functions:

    think(): This function simulates a philosopher thinking by putting the thread to sleep for a random amount of time.
    pickup_forks(): This function is called by a philosopher when they want to pick up their forks. 
    
    It acquires the mutex lock and checks to see if the philosopher's forks are available. 
    
    If the forks are not available, the philosopher is blocked until they are released. 
    If the forks are available, the philosopher picks them up and changes their state to "EATING".
    eat(): This function simulates a philosopher eating by putting the thread to sleep for a random amount of time.
    return_forks(): This function is called by a philosopher when they are finished eating. 
    It releases the mutex lock and signals any philosophers that are blocked on their conditional variable, 
    allowing them to check if they can pick up their forks.
    philosopher(): This is the main function for the philosopher threads. It simulates the philosopher thinking, 
    picking up their forks, eating, and putting down their forks in a loop.

Overall, this code uses concurrency and synchronization tools to solve the Dining Philosophers Problem in a way that avoids deadlocks.
