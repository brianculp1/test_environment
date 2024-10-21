
# Verify CPU capabiltiy & BIOS Setup
* lscpu | grep Virtualization
* lsmod | grep kvm # should show both kvm and kvm_intel
* kvm-ok # should show "acceleration can be used"

# Install packages
* sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients virt-manager

# Setup user in right group & enable rootless vm access
* sudo adduser serveradmin kvm
* sudo adduser serveradmin wheel
* sudo cp -rv /etc/libvirt/libvirt.conf ~/.config/libvirt/ && 
* sudo chown serveradmin:serveradmin ~/.config/libvirt/libvirt.conf
* reboot

# Setup bridged network
## Create the net device
```
[NetDev]
Name=br0
Kind=bridge
```

## Setup the binding
```
[Match]
Name=eno1
[Network]
Bridge=br0
```

## Setup dhcp on br0
```
[Match]
Name=br0
[Network]
DHCP=ipv4
```





