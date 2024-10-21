## Usage
- Run KVM gui: virt-manager
- List VMs: virsh list --all
- List Networks: virsh net-list --all

### VM show/change config: 
  - list block devices: virsh domblklist <domain> --details
  - Edit a VM: sudo virsh edit <domain>
  - Dump existing VMs settings: virsh dumpxml <domain>
  - VM HW Info: virsh dominfo <vm>
  - Register: virsh define /etc/libvirt/qemu/<vm>.xml
  - Register & Start: virsh create /etc/libvirt/qemu/<vm>.xml
  - Delete xml file and unregister: virsh undefine <vm>
### VM state changes
  - Eject CD: virsh change-media <domain> sda --eject
  - Load CD: virsh change-media <domain> sda <path_to_iso> --insert
  - Start VM: sudo virsh start <domain>
  - Shutdown VM: sudo virsh shutdown <domain>
  - Force Shutdown VM: sudo virsh destroy <domain>
  - Autostart VM: virsh autostart <domain>
### VM management
  - VM Console: virsh console <vm> # FIXME not working via vnc
  - VM vnc: virsh vncdisplay <vm> # FIXME not working via vnc
### Paths
  - VM xmls are kept in /etc/libvirt/qemu
  - VM xmls are kept in /etc/libvirt/qemu/autostart
  - VM data is kept in /var/lib/docker/kvm_storage
### Snapshots
  - List snapshots for a domain: virsh snapshot-list --domain opensleseserver
  - List detailed snapshot info: virsh snapshot-info --domain openslesserver --snapshotname 04_oct_2024_s0
  - Create snapshot (if running): virsh snapshot-create-as --domain openslesserver --name "04_oct_2024_s0" --description "pre upgrade" --live
    - If shutdown, leave off the --live
    - If running, to capture disk but not vm state, add --disk-only.
  - Revert: virsh snapshot-revert --domain openslesserver --snapshotname 04_oct_2024_s0 --running
  - Delete a snapshot: virsh snapshot-delete --domain openslesserver --snapshotname 04_oct_2024_s0

## Install guides
- https://cmdref.net/middleware/virtualization/kvm/install_guest_with_virt-install.html
- https://cmdref.net/middleware/virtualization/kvm/index.html
- For ubuntu v20, try:  https://ubuntu.com/blog/kvm-hyphervisor
