# Passthrough of a Single GPU for use on a VM - Ubuntu
# Grub Configuration
Open your system terminal.

Run `sudo nano /etc/default/grub` in your terminal.

This is the configuration file for the grub boot loader. This application is similar to the Windows Boot Manager, as it directs your computer on booting linux. We need to change some values for our kernal.

Find the line that starts with `GRUB_CMD_LINE_LINUX_DEFAULT`. You can press `Ctrl-W` for a search function in the nano editor.

This line likely says `quiet splash` if you haven't previously changed your grub configuration. Leave these. `splash` shows the splash screen for your OS during boot, and `quiet` helps silence some output from the system during boot that would disrupt the splashscreen.

For AMD Processors, append the following arguments to the front of string: `amd_iommu=on iommu=on video=efifb:off`

For Intel Processors, append the following arguments to the front of the string: `intel_iommu=on iommu=on video=efifb:off`

In my case, my grub file now looks like this:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=on video=efifb:off quiet splash"
GRUB_CMDLINE_LINUX=""
```

Press `Ctrl-S` to save, then `Ctrl-X` to exit.

Run `sudo update-grub`. This will update the grub boot loader based on the configuration we have just edited.

Reboot your system using `sudo reboot`. This is neccessary for the configuration changes to take effect, so don't skip it.


[Home](/ubuntu-kvm-gpu-passthrough/)  
[Previous](/ubuntu-kvm-gpu-passthrough/bios)  
[Next](/ubuntu-kvm-gpu-passthrough/iommu-groups/)