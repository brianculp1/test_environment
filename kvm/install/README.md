### Example to create a new VM 
```
virt-install  \
  --name opensusetumbleweed2 \
  --ram 8192 \
  --disk path=/var/lib/docker/kvm_storage/opensusetumbleweed2.qcow2,size=30 \
  --vcpus 2 \
  --os-variant opensusetumbleweed \
  --console pty,target_type=serial \
  --bridge=br0 \
  --cdrom /opt/downloads/isos/template/iso/openSUSE-Tumbleweed-DVD-x86_64-Snapshot20240813-Media.iso
```

### clone a VM
- Ensure unique machine ID.  Always do this before you shutdown a VM for cloning.
  - echo -n > /etc/machine-id
- Clear user histories, bash, etc.
- Blank out /etc/hostname

```
virt-clone  \
  --original opensusetumbleweed1 \
  --name opensusetumbleweed3 \
  --file /var/lib/docker/kvm_storage/opensusetumbleweed3.qcow2
```
- In the first boot after cloning, set it


