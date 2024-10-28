

# Qemu Crazy

Howdy Wizards, 

Quick and dirty hit on how to go from OVA to Proxmox VM with no fuss.

I downloaded the VM to the baremetal server,

```shell
qemu-img convert -O qcow2 diskhere.ova diskdesiredname.qcow2
```

Make a VM with no OS and no disk now the number of the VM you just make will be used below where you see the ###

Needed Variables
!!! -> Storage Location
/### -> VMID number which the drive will be mounted onto


```bash
qm importdisk ### ./diskdesiredname.qcow2 !!!
```

Now on the GUI when you go to your empty VM you should see an unused Disk. Double click the sucker and add it as a sata in the Bus/Device setting.