# cmpe283-assignment2-modifying-cpuid-exit-handler

** Steps Used To Build And Complete This Assignment **

Prerequisites: Use virtualization enabled machine with at least 160-200 GB space.

Step 1: Get VMware Fusion setup installed.

Step 2: Then install Linux Ubuntu on VMware Fusion. Enable nested virtualization.

Step 3: Then install GitHub on a laptop.

Step 4: Clone the kernel sources from the master Linux git repository:
git clone https://github.com/torvalds/linux.git

Step 5: Build the kernel, Install packages necessary to compile the Linux kernel from source:
        ---> sudo bash apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev

Step 6: Print all the system information in the following order: Kernel name, network node hostname, kernel release date, kernel version, machine hardware name, hardware                 platform, operating system. This can be done by running the follwo
         ---> "uname -a"

Step 7: Execute the following commands sequentially one after the other
       --->  cp /boot/config-4.15.0-112-generic ./.config (substitute your version obtained from the previous step here though)
       --->  make oldconfig
       --->  make && make modules && make install && make modules-install 
       --->  Reboot
        Verify that you are using the newer kernel after reboot: 
       ---> uname -a

Step 8: Modify the kernel code with the assignment functionality: ◦ 

Step 9: After modifying the code both in cpuid.c and vmx.c do the following steps again 
       
         ---> make oldconfig
        
        ---> make && make modules && make install && make modules-install 
        
        ---> Reboot

Step 9: Now to test this change to CPUID.c create an inner VM.
       
       
 a) Use the following command to install KVM and supporting packages.	
        ---> sudo apt-get install qemu-kvm libvirt-bin bridge-utils virt-manager
 
 b) Verify KVM Installation using the following command. You should see an empty list of virtual machines. This indicates that everything is working correctly.
        ---> virsh -c qemu:///system list
  
  c) Install Virt-Manager
        ---> sudo apt-get install virt-manager
   
  d) Install CPUID by using the following command
        ---> sudo apt-get install cupid
        ---> CPUID gives a whole list of CPUID features of which the first one is the vendor string.
        
   e) Run CPUID-l-0x4FFFFFFF
        ---> It gives the information for eax,ebx,ecx values
        ---> Where it gives eax =total exits :  ebx =total cycle count of hi bit value: ecx =total cycle count of low bit value
 
 







