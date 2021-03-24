# Passthrough of a Single GPU for use on a VM - Ubuntu
# BIOS Changes
Reboot and enter your bios. Change the CPU Configuration and ensure the following are enabled:  
For AMD Processors:
+ IOMMU = enabled or on
+ NX MODE = enabled or on
+ SVM MODE = enabled or on  

For Intel Processors:
+ VT-D = enabled or on
+ VT-X = enabled or on

[Home](/ubuntu-kvm-gpu-passthrough/)  
[Previous](/ubuntu-kvm-gpu-passthrough/prerequisites)  
[Next](/ubuntu-kvm-gpu-passthrough/grub-configuration/)