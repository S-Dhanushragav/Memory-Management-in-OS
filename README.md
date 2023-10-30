# Memory-Management-in-OS
Implemented a memory management simulation using First-Fit allocation and deallocation algorithms. The program dynamically allocates and deallocates memory blocks for processes, tracking fragmentation and wasted memory. Provides insights into memory usage, aiding analysis and comparison under different scenarios.
# INTRODUCTION:
In the realm of computing, memory serves as a fundamental component, providing the digital space where programs and data reside during execution. Within this memory space, data is stored in memory blocks, discrete segments that represent allocatable units within the system. Processes, on the other hand, are the running instances of programs, each requiring a portion of the available memory to function.

To manage the allocation of memory blocks to processes effectively, various algorithms have been developed. One such algorithm, the First-Fit algorithm, is employed to allocate memory blocks sequentially. When a new process is to be allocated, the First-Fit algorithm searches the memory blocks and selects the first block that adequately accommodates the process size.

Memory allocation involves the process of assigning these memory blocks to running processes, ensuring efficient utilization of the available space. This allocation is critical for the seamless execution of programs, as it directly impacts the system's performance.

In the life cycle of a process, memory deallocation becomes crucial upon completion or termination. Deallocating memory involves releasing previously allocated memory blocks, allowing them to be reused for new processes. Effective deallocation mechanisms prevent unnecessary wastage of memory resources.

However, continuous allocation and deallocation processes may lead to a phenomenon known as fragmentation. Fragmentation occurs when the memory space is broken into small, non-contiguous blocks, making it challenging to allocate memory for larger processes even when sufficient memory exists in total. This fragmentation can lead to inefficiencies in memory usage.

Additionally, it’s essential to consider wasted memory, referring to memory blocks that are no longer utilized by any processes. Calculating wasted memory involves identifying and quantifying these unutilized blocks, providing insights into memory management efficiency.
In this project, we delve into these fundamental concepts, exploring the intricacies of memory allocation, deallocation, fragmentation, and wasted memory. By implementing and simulating the First-Fit algorithm, we aim to gain practical insights into these vital aspects of memory management, enabling a deeper understanding of their impact on computational systems.

# SOLUTION APPROACH:
The solution was approached by implementing the First-Fit memory allocation algorithm. The program initializes memory with the given total size and processes. It allocates memory to processes based on the First-Fit algorithm, splits blocks if needed, and deallocates memory upon process completion. Fragmentation and wasted memory are calculated by iterating through memory blocks, and the simulation results are displayed after each operation.

## Memory Block and Process Representation:
Memory Block Structure: A structure was defined to represent memory blocks. Each block contains information such as start address, size, allocation status, and associated process ID.
Process Structure: Another structure was defined to represent processes. Each process has a unique identifier and a specified size.

## Memory Allocation and Deallocation:
First-Fit Algorithm: The First-Fit algorithm was chosen for memory allocation. It scans the memory blocks sequentially and selects the first block that fits the size of the process to be allocated.
Memory Allocation Function: A function (allocateMemory) was implemented to allocate memory to processes using the First-Fit algorithm. It handles both memory allocation and splitting blocks if necessary.
Memory Deallocation Function: A function (deallocateMemory) was implemented to deallocate memory used by a specific process. It marks the corresponding memory block as unallocated and merges adjacent free blocks to prevent fragmentation.

## Output and Analysis:
Memory Status Visualization: The program outputs the memory status before and after each allocation and deallocation operation. Memory blocks are displayed in a formatted table-like structure, making it easy to visualize the memory allocation.
Fragmentation and Wasted Memory Calculation: Fragmentation (unused memory within allocated blocks) and wasted memory (unused memory blocks) are calculated and displayed before and after the deallocation operation. These metrics provide insights into memory utilization efficiency.

# PSEUDOCODE:
1. Start
2. Input totalMemorySize
3. Initialize memory block:
   - Set startAddress = 0
   - Set size = totalMemorySize
   - Set allocated = 0
   - Set processID = -1
   - Set next = NULL
4. Input numberOfProcesses
5. For each process from 1 to numberOfProcesses:
   a. Input processSize
   b. Create new Process structure with processID = current process number and size = processSize 
6. Print initial memory status
7. For each process from 1 to numberOfProcesses:
   a. Initialize current as the first memory block
   b. While current is not NULL:
      i. If current is unallocated and current size >= process size:
         - Mark current as allocated for the current process
         - If current size > process size:
           - Split current block into two:
             - One with size = process size and allocated for the current process
             - Another with size = current size - process size and unallocated
         - Break the loop
      ii. Move to the next memory block
8. Print memory status after each allocation
9. Deallocate memory for a specific process (e.g., processIDToDeallocate)
   a. Initialize current as the first memory block
   b. While current is not NULL:
      i. If current is allocated and processID matches processIDToDeallocate:
         - Mark current as unallocated
         - Merge adjacent free blocks:
           - While next block is unallocated:
             - Add its size to the current block
             - Set current's next pointer to next block's next
             - Free next block
         - Break the loop
      ii. Move to the next memory block
10. Print memory status after deallocation
11. Calculate and print fragmentation and wasted memory
12. Free allocated memory blocks
13. End

# CONCLUSION: 

In conclusion, the implemented memory management simulation program successfully addresses the requirements outlined in the initial question. The program efficiently allocates and deallocates memory blocks using the First-Fit algorithm. It maintains the memory status in a clear and organized manner, displaying allocated and unallocated blocks along with their corresponding start addresses, sizes, allocation status, and process IDs.

The simulation accurately calculates and reports fragmentation, which occurs when there are small, unused memory blocks scattered throughout the memory space. Additionally, the program tracks wasted memory blocks, representing blocks that are no longer used by any processes.

Throughout the simulation, the program provides a comprehensive view of the memory status, fragmentation, and wasted memory before and after memory allocation and deallocation operations. It allows for dynamic user input, making it adaptable to different memory sizes and various numbers of processes.

By offering a practical implementation of memory management, this program serves as an educational tool for understanding the complexities involved in memory allocation algorithms. Users can experiment with different input scenarios, enabling a comparative analysis of the program's performance under various conditions.

In summary, this memory management simulation program not only meets the specified project requirements but also provides a foundation for further exploration and experimentation with different memory allocation strategies, contributing to a deeper understanding of computer memory management systems.
