# SE23MAID012_2
# Concurrent Double-Linked List

## Introduction

This Java program implements a concurrent double-linked list data structure and evaluates its performance using different synchronization techniques. The program tests various problem sizes, thread counts, and workloads to measure the efficiency of the concurrent data structure.

### Synchronization Techniques

1. *Coarse-Grain Synchronization*: The entire list is locked during each operation, allowing only one thread to access the list at a time.

2. *Fine-Grain Synchronization*: Locks are applied at a more granular level, typically per-node or per-section, allowing multiple threads to access different parts of the list simultaneously.

3. *Optimistic Synchronization*: It uses a combination of optimistic reading and CAS (Compare-and-Swap) to perform operations with minimal locking.

4. *Lazy Synchronization*: Operations are initially executed without synchronization, and synchronization is applied only when conflicts are detected.

5. *Non-Blocking Synchronization*: Uses atomic operations and CAS to perform operations without traditional locks, ensuring non-blocking concurrent access.

## Workloads

Three types of workloads are defined:

1. *0C-0I-50D (Workload 1)*
   - 0% Inserts, 0% Reads, 50% Deletes
   - Simulates a workload with mostly delete operations.

2. *50C-25I-25D (Workload 2)*
   - 50% Inserts, 25% Reads, 25% Deletes
   - A mixed workload with a balanced combination of operations.

3. *100C-0I-0D (Workload 3)*
   - 100% Reads, 0% Inserts, 0% Deletes
   - Simulates a workload with only read operations.

## Execution

1. Compile the Java code:
   bash
    javac ConcurrentLinkedListTest.java
   

2. Run the tests using the following command:

   bash
    java ConcurrentLinkedListTest <problemSize> <numThreads> <workload>
   

   Example : 

   bash
    java ConcurrentLinkedListTest 2000 2 "50C-25I-25D"
   

3. The program will execute tests for various problem sizes (2 x 10^3, 2 x 10^4, 2 x 10^5), thread counts (1, 2, 4, 6, 8, 10, 12, 14, 16), and workloads (0C-0I-50D, 50C-25I-25D, 100C-0I-0D).

## Results

The program will print the following results to the console:

- Problem size, thread count, workload, execution time, and throughput for each configuration.

## Graphs of the syncronization technique(Threads vs Throughput):

1. *Coarse-Grain Synchronization*:
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/f18c604d-08a8-4fa4-9023-bde94090db87)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/760b4037-ac54-46fa-8d77-bd9d1d014534)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/7c2e6b54-4ac3-45d4-88fd-ef521d6a7236)

   

2. *Fine-Grain Synchronization*:
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/ee3570b2-fab7-4b4f-a54b-2194e9867b45)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/dbeb33fa-0ce7-4c91-b6ab-1d1e7756aec1)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/74bce540-7976-4ae0-88d4-7279e9641e44)
	


3. *Optimistic Synchronization*:
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/3547ade8-44de-4457-b192-b37b54eb43ad)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/258ff16a-98dd-4d3a-9529-67de1f1e4a08)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/2fbf1fec-0a22-4b84-b44d-4c96dbaba807)
   


5. *Lazy Synchronization*:
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/a00e08d2-9263-4c5a-b0f4-1dfce50b702a)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/74e29339-60f2-412f-a2ae-292e064ce793)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/d026a19e-36fd-426b-8c9d-93d8cc41cca0)



7. *Non-blocking Synchronization*:
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/d77eca97-3f53-49bf-a062-3d1d1d41f059)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/8d2e890f-faa4-4087-9962-a462dcda007a)
![image](https://github.com/JyothiNarsini/SE23MAID012_2/assets/88646255/900a496a-89c4-4ba7-858e-add4f537c77e)


## Conclusion

In this project, we explored the implementation of a concurrent double-linked list data structure with various synchronization techniques. The goal was to evaluate the performance of these techniques under different scenarios, including varying problem sizes, thread counts, and workloads.

Here are some key takeaways from our experiments:

- Coarse-grain synchronization, while easy to implement, often leads to contention, limiting concurrency and performance.

- Fine-grain synchronization provides better concurrency by allowing multiple threads to access different parts of the list simultaneously, but it can be complex to implement correctly.

- Optimistic synchronization, relying on optimistic reading and CAS operations, can offer high concurrency and performance, especially in scenarios with low contention.

- Lazy synchronization, which defers synchronization until conflicts occur, can be efficient when conflicts are infrequent but may suffer in high-contention situations.

- Non-blocking synchronization, using atomic operations and CAS, can provide non-blocking access and high concurrency but requires careful implementation.

The choice of synchronization technique should be based on the specific requirements of your application and the characteristics of your workload. It's important to balance ease of implementation with performance optimization, depending on the use case.
