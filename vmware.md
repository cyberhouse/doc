# How-Tos
## Get Top-Like Stats for ESX Server

	TERM=xterm esxtop

## Suspend Virtual Machine from Command Line

	vmrun suspend /data1/virtual-machines/vm1.vmx

## Copying Virtual Disk Files
1. Consolidate snapshots (if any)
2. ``vmware-cmd </vmfs/volumes/.../cfg.vmx> stop`` 
3. ``vmkfstools -i <src.vmdk> <dst>``

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
