# Comparison between Cubic and BBR

In this experiment, I reproduced the graphs from following two blogs.

1. https://reproducingnetworkresearch.wordpress.com/2017/06/05/rebbr/
2. https://reproducingnetworkresearch.wordpress.com/2017/06/05/cs-244-17-congestion-based-congestion-control-with-bbr/

Follow the instructions below to reproduce the experiements from the blog 1.

## Blog 1 Experiment reproduction

To run the experiment, we will create one vm with Linux kernel that includes congestion control "bbr". It will take around 7 hours to run all the experiments.

### Set up the VM

Perform the following steps to create the VM

 1. Install Oracle VM VirtualBox
 2. Create a new machine with Ubuntu 16.04.7 LTS (ISO download link: https://releases.ubuntu.com/16.04/)
 3. VM configuration: Base Memory-2048 MB, Processors-2, Storage-25 GB. You can add more resources if available



### Dependency Installation

 1. Login or SSH to the machine.
 2. Clone the repository into the bbr folder.
 ```
 git clone https://https:github.com/jervisfm/rebbr.git bbr
 
 ```


