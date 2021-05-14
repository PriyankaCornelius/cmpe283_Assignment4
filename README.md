# cmpe283_Assignment4

## Steps followed :

1.Working environment of Assignment3.

2.Inside inner VM, run the test code for exit reason values from 0 to 68 present in ecx

    cpuid -l 0x4FFFFFFE -s
    
3.Store the output in a file.

4.Shutdown inner VM

5.Change directory to the path /lib/modules/5.12.0-rc8+/kernel/arch/x86/kvm.

6.Using below command, remove the kvm-intel module :

     sudo rmmod kvm-intel
     
7.Reload kvm-intel module with the parameter ept=0 

8.Using below command, insert the kvm-intel module :
    
    sudo insmod kvm-intel.ko ept=0

9.Inside inner VM, run the test code for exit reason values from 0 to 68 present in ecx

    cpuid -l 0x4FFFFFFE -s
    
10.Store the output in a file.

### What did you learn from the count of exits? Was the count what you expected? If not, why not?

    Exit count is more for shadow paging compared to nested paging since the VMM performs more work in case of shadow paging.

### What changed between the two runs (ept vs no-ept)?

    During shadow paging i.e.ept=0 , VM performs more TLB flushes, page faults etc. and so their are more exits comapred to ept=1.
