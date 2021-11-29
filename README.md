# Assignment 3 READ ME 
1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched. (You may skip this question if you are doing the lab by yourself).
I am doing this lab by myself

2. Describe in detail the steps you used to complete the assignment. Consider your reader to be someone 
skilled in software development but otherwise unfamiliar with the assignment. Good answers to this 
question will be recipes that someone can follow to reproduce your development steps.

1. update the cloned directory from assignemnt 2 for the updated cpuid.c and vmx.c
2. in the directory linux  
    $ cd linux
    $ sudo apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev 
    $ sudo apt-get install qemu-kvm libvirt-bin bridge-utils virt-manager
    $ sudo uname -a (use the version instead of "linux-version"
    $ sudo cp /boot/config-"linux-version" ./.config
    $ sudo make old config
    $ sudo make 
    $ make INSTALL_MOD_STRIP=1 modules_install && make install
    $reboot (to see the changes)
3. Creating a vm inside the VM
    virsh -c qemu:///system list (should see 0 VMS intially)
4. Boot the test VM and check with a user program for CPUID values

3. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there 
more exits performed during certain VM operations? Approximately how many exits does a full VM 
boot entail?

The number of exits is the opposite of stable and is very sporatic, where there is a huge gap between the occurances of some specific exits and others. Thus there are more exits performed suring certain VM operations. In this VM the total exits are: 500K.

4. Of the exit types defined in the SDM, which are the most frequent? Least?
Of the Exits defined in the SDM, the most frequent is the externel interupt and the least is MOV DR

# Assignment 2 READ ME 
1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched. (You may skip this question if you are doing the lab by yourself).
I am doing this lab by myself

2. Describe in detail the steps you used to complete the assignment. Consider your reader to be someone 
skilled in software development but otherwise unfamiliar with the assignment. Good answers to this 
question will be recipes that someone can follow to reproduce your development steps.

1. update the cloned directory from assignemnt 1 for the updated cpuid.c and vmx.c
2. in the directory linux  
    $ cd linux
    $ make -j nproc modules 
    $ sudo bash (so we dont need to make everything sudo)
    $ make INSTALL_MOD_STRIP=1 modules_install && make install
    $ lsmod | grep kvm
    $ rmmod kvm_intel
    $ rmmod kvm
    $ lsmod | grep kvm
    $ modprobe kvm
    $ lsmod | grep kvm
    $ modprobe kvm_intel
    $ lsmod | grep kvm
3. Creating a vm inside the VM
    sudo apt-get install qemu-kvm libvirt-bin bridge-utils virt-manager
    virsh -c qemu:///system list (should see 0 VMS intially)
4. Boot the test VM and check the dmesg in intial VM 

# Assignment 1 READ ME 

1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched. (You may skip this question if you are doing the lab by yourself).

I had done this lab by myself

2. Describe in detail the steps you used to complete the assignment. Consider your reader to be someone 
skilled in software development but otherwise unfamiliar with the assignment. Good answers to this 
question will be recipes that someone can follow to reproduce your development steps.
Note: I may decide to follow these instructions for random assignments, so you should make sure 
they are accurate.

1. Go into the Terminal 

2. clone the Linux github
2a. Fork the offical linux github (https://github.com/torvalds/linux)
2b. clone the forked github into the Terminal i.e git clone "insert url"
ignore steps 2 and 2a, since the clone of this repo will have the updated linux and the sub folder with makefile and skeleton file

3.Making a new Linux Kernel
3a. cd linux (go to the new cloned folder for linux)
3b.cp /boot/config-5. (check the version of the config)
3c.Create a config 
    cp /boot/config-5.xx.x+ .config
3d. Need to make it newer
    make old config
3e. HOLD ENTER till you see the command line input
3f. make prepare

4. check if worked
4a. cd ..
4b. make
4c. make clean

5.Build a new Kernel
5a. cd linux
5b.make -j "number of cpu" modules
5c.make kernel
  make -j "number of cpus"
  
6.Package kernel
6a. sudo make INSTALL_MOD_STRIP=1 modules_install

7. Install Kernel
sudo make install
sudo reboot

8.Check 
uname -a (see if it was rebooted correctly)

9. adding module licsence (not needed as the .c file already has it)
9a. make

10. Load code into Kernel
10a. sudo insmod cmpe283-1.ko

11. see the messages
11a. demsg
11b. see the messages (see cmpe283-1.jpeg and cmpe283-1-2.jpeg)


    
