---
title: Building a Simple CPU Scheduler
categories: [Projects]
tags: [projects, advanced-operating-systems, programming]     # TAG names should always be lowercase
---

# Overview
This project leverages Azure, a few virtual machines (including some nested ones!) and the libvirt library. Each nested VM thinks that it is running on it's own virtual CPU (VCPU), but thanks to the wonders of virtualization, each VCPU is running on a physical CPU (PCPU). Since virtualization allows you to take a single machine and essentially make it act like multiple machines, it is common to have the number of PCPUs < the number of VCPUs. The goal is to ensure that each physical CPU (PCPU) runs as close to a balanced load (in % usage) as possible. Libvirt is leveraged to collected VM and host usage statistics to facilitate the determination of an optimal "pinning" or mapping of VCPU to PCPU.

# Considerations
- The scheduler should keep the PCPU usage balanced, if possible. This balanced approach comes from the somewhat naive thought process that that no particular PCPU should be either over- or under-utilized.
- The scheduler should also be stable, in that it does not frequently remap VCPUs to different PCPUs unless there is a dire need to. In this context, a "dire need" would be that we have determined a particular PCPU is overloaded and another underutilized PCPU exists. This helps to keep the explicit and implicit costs of PCPU changes down. Every time a remapping is done, the VCPU sees a new processor, cold cache, cold TLB...not to mention all of the kernel overhead involved.

# Limitations
In practice, CPU utilization might be one of, but not the only, indicators that would prompt us to make a decision about remapping. 

# Algorithm Overview
- Struct for holding information about domains (VCPUs)
- Struct for holding information about PCPUs
    - Data is in header file. It is essentially CPU Time for the current and previous iteration, as well as the domain, and some IDs.


- Usage (as a percentage) is calculated on each run for both the VCPUs and PCPUs. 
    - The calculation is (currTime - prevTime) / interval.
- PCPU utilization is determined by summing up the usage of all of the VMs currently pinned to that PCPU.
- If the difference between the most and least utilized PCPU is above a threshold (12, in units of percentage), we rebalance
- Rebalancing is done on a greedy basis
    - Pinnings are assigned by using the PCPU as an "empty bin"
    - A PCPU bin has a sum
        - The sum is defined as the total percentage of all of the VCPUs currently in that bin
    - The highest usage VCPUs are greedily allocated to the bin with the lowest current sum
    - Each time we allocate a VCPU to a "bin", we resort the bins from smallest to largest sum
        - This is done with qsort(). Since the number of bins is low, the sort overhead time complexity is low and I considered it tolerable for this algorithm.

- Some noise may be present (occasional transient spikes), so a counter is used that can range from 0 to 3 and is dynamically set/reset each iteration
    - If there is "sufficient imbalance" for three consecutive iterations of the scheduler, we finally rebalance and reset the counter to 0
    - Three seconds was chosen based on the assumption that the scheduler is running once per second
        - If load increases for more than 3 seconds, it is probably indicative of a real increased load

## Known Limitations
- The scheduler will not balance VCPUs when the number of VCPUs is less than the number of PCPUs
    - This is done to avoid repinning a workload (which will incur a performance cost) since for the purposes of this test, any single PCPU is considered just as viable as any other
- The VCPU will repin "impossible-to-balance" loads over and over. In this toy problem, all tests will contain VCPU workloads that should theoretically balance across all PCPUs.
    - I could implement this by checking a "theoretical sort order" and only accept it (and complete the repinnings) if the theoretical sort has a smaller max-min difference that the current real pinning.




<!-- ## Requirements
- Persistent storage of job application records
- Should be able to track which specific resume was used, for future reference
- Should allow for additional notes to be attached to an application
- Should keep track of date applied
- Should track application and interview progress -->



