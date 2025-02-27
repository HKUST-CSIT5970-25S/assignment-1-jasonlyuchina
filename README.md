[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IAASVEAZ)
# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: LYU Peiduo
### Student Id: 21135389
### Email: plyuac@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    I use the **Phoronix Test Suit** as the measurement tool.
   
    For the CPU Benchmark, we use the **compress-7zip** as the test to use the compression and decompression performance as a CPU benchmark.

    It does not have any parameter except from the output related commands.
   
    The result is the Compression Rating and Decompression Rating of three separate trial run and the average of three rating.
   
    **In the next question, we only use the compression Rating as the performance benchmark**

    For the memory Benchmark, we use the **ramspeed** as the test to use the copy performance on integer as a memorhy benchmark.

    We provide the **copy** and **integer** as the parameter to ask the test suite to do the test with copy and integer.

    The result is the memory bandwidth of the server in three separate trials together with an average of three bandwidth.
    

3. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance(MIPS) | Memory performance(MB/s) |
    | ----------- | --------------- | ------------------ |
    | `t2.micro` | 4235  | 11317.28  |
    | `t2.medium`  | 9969 |19535.73 |
    | `c5d.large` | 7453  | 13592.11 |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI.
    
    **Yes, we can see that for the t2.micro it have 1 vcpu with 1 core, and 1 GB RAM, for the t2.medium, it have 2 vcpu with 2 core each, and 4GB RAM, for the c5d.large, it have 2 vcpu with 1 core each, and 4GB RAM. We can see that with the more vCPUs and more memory resource, the performance of EC2 increases.**

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | `t3.medium` - `t3.medium` | 3310  | 0.272 |
    | `m5.large` - `m5.large`   |4960  |0.132 |
    | `c5n.large` - `c5n.large` | 4960 | 0.299 |
    | `t3.medium` - `c5n.large` |2010 |0.828 |
    | `m5.large` - `c5n.large`  | 4960  |0.125 |
    | `m5.large` - `t3.medium`  |2170 | 0.685 |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

    **For the bandwidth, between the same type of instance is better than or equal to between the different types of instance.**
   
    **For the RTT, between the same type of instance is better than or equal to between the different types of instance under most of the conditions.**

3. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      |   32.5  |  63.05 |
    | N. Virginia - N. Virginia |  4300  | 0.217 |
    | Oregon - Oregon           |  4430|0.181  |
 
    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.

    **The network performance for instances deployed in different region is much worse(slower) than which in the same region**
