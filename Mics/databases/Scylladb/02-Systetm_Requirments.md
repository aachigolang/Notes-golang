

### Hardware Requirements


Installation 			Cores 		Memory 		Disk 				Network
Test, minimal 			4 			2 GB 		Single plain SSD 	1 Gbps
Production 				20 cores - 2 socket, 10 cores each 	128 GB 	RAID-0, 4 SSDs, 1-5 TBs 	10 Gbps
Analytics, heavy duty 	28 cores - 2 socket, 14 cores each 	256 GB - 1 TB 	NVMe, 10 TB 	10-56 Gbps


#### CPU
Scylla requires modern Intel CPUs that support the SSE4.2 instruction set and will not boot without it.
Between 20-60 logical cores (including hyperthreading) is a recommended number

#### Memory

    Recommended size: 16 GB or 2GB per lcore (whichever is higher)
    Maximum: 1 TiB per lcore, up to 256 lcores
    Minimum:
        For test environments: 1 GB or 256 MiB per lcore (whichever is higher)
        For production environments: 4 GB or 0.5 GB per lcore (whichever is higher)


#### Disk
We highly recommend SSD and local disks
The rule of thumb is using 30:1 Disk/RAM ratio
we recommend a RAID-0 setup and a replication factor of 3 within the local datacenter (RF=3).

HDDs are supported but may become a bottleneck
an HDD-friendly workload is a write-mostly (98% writes) workload, with minimal random reads. 

#### Network
Network speed of 10 Gbps or more is recommended

### Cloud Recommendations
We highly recommend EC2 I3 instances—High I/O. i3.xlarge e.t.c.


