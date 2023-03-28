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



### Installation & Running Experiments

1. Login or SSH to the machine.
2. Clone the repository into the bbr folder.
 ```
 git clone https://https:github.com/jervisfm/rebbr.git bbr
 ```
3. Give permission to the "bbr" folder
 ```
 sudo chmod -R 777 bbr *
 ```
4. Change the content of the file vm_upgrade_kernel.sh with the following.
 ```
 set +x
 cd /tmp/

 wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/linux-headers-4.11.0-041100_4.11.0-041100.201705041534_all.deb

 wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/linux-headers-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb

 wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/linux-image-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb

 echo "Installing new kernel. Will be prompted to enter password"
 sudo dpkg -i *.deb

 rm -f *.deb
 echo "Reboot the Machine and verify installation with uname -sr
 ```
5. Run the following command to install the kernel 4.11.0
 ```
 cd bbr && ./vm_upgrade_kernel.sh
 ```
6. Run the following command to see the kernel is installed on your vm.
 ```
 dpkg --list | grep linux-image
 ```
 This should give you the list of the kernels available in your vm.
 
7. now reboot the machine
 ```
 sudo reboot
 ```
8. Reboot with "Advanced Loader Options". Then you should get a list of the kernels. Select linux-image 4.11.0 generic+ and boot
9. Once logged in, verify the kernel with the following kernel.
 ```
 uname -sr
 ```
10. if it does not give Linux "4.11.1-041101-generic", repeat from step 5.
11. Run the following commag command to make bbr congestion control available.
 ```
 sudo modprobe tcp_bbr
 ```
12. change the following line in mahimahi/init_deps.sh file
 ```
 pip install matplotlib
      to 
 sudo apt-get install python-matplotlib 
 ```
13. Now, run the following command to run the experiments.
 ```
 sudo ./run_all.sh
 ```
14. You can also run the individual experiments with the following commands
 ```
 sudo ./run_figure8_experiment.sh
 sudo ./run_experiment1.sh
 sudo ./run_experiment2.sh
 sudo ./run_experiment3.sh
 sudo ./run_experiment4.sh
 ```
15. It will take around 7 hours to complete the experiment. Once finished, results can be viewed in the following folders.
 1. data - All the data for the experiments will be generated here.
 2. figures -  All the figures will be generated here.  


This will conculde the experiment.
