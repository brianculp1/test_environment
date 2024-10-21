* Enable virtualization in BIOS, if necessary
* Verify enabled: 
  * lscpu | grep Virtualization
  * lsmod | grep kvm # should show both kvm and kvm_intel
  * kvm-ok # should show "acceleration can be used"
* Install packages: sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients virt-manager
* Add yourself to kvm group: sudo adduser serveradmin kvm
* To enable rootless root vm access
  * sudo cp -rv /etc/libvirt/libvirt.conf ~/.config/libvirt/ && 
  * sudo chown serveradmin:serveradmin ~/.config/libvirt/libvirt.conf
  * assumes serveradmin is a member of an admin group
* reboot
