link1: [How to Install KVM and QEMU on Ubuntu Server](https://oneuptime.com/blog/post/2026-03-02-install-kvm-qemu-ubuntu-server/view)
link2: [Setting up Windows 10 in QEmu](https://rtbecard.gitlab.io/2022/07/23/QEmu_win10.html)
link3: [How to get the best experience from Windows guests under Linux KVM - pauby.com](https://blog.pauby.com/post/howto-best-windows-guests-linux-kvm-qemu/#mount-virt-winiso-on-the-cdrom-install-the-virtio-tools-and-dismount-the-iso)
link4: [Share Folder Between Windows Guest and Linux Host in KVM using virtiofs](https://www.debugpoint.com/kvm-share-folder-windows-guest/)

## install KVM
```bash
sudo apt update
sudo apt install -y \
  qemu-kvm \
  libvirt-daemon-system \
  libvirt-clients \
  bridge-utils \
  virtinst \
  virt-manager \
  libguestfs-tools
  
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER

sudo systemctl start libvirtd
sudo systemctl enable libvirtd
sudo systemctl status libvirtd

virt-manager &
```
## create win 10 
```
[Windows 10 Download | MAS](https://massgrave.dev/windows_10_links)
version: Windows 10 pro 22H2

NIC active choose no if don't want network
```
![[Pasted image 20260521175935.png]]
![[Pasted image 20260521180042.png]]
![[Pasted image 20260521180147.png]]
![[Pasted image 20260521180350.png]]
![[Pasted image 20260521180442.png]]
![[Pasted image 20260521180506.png]]![[Pasted image 20260521180530.png]]
![[Pasted image 20260521180648.png]]
![[Pasted image 20260521180736.png]]
![[Pasted image 20260521180839.png]]
![[Pasted image 20260521180932.png]]
## filesystem share
![[Pasted image 20260521181338.png]]
![[Pasted image 20260521181422.png]]
windows install WinFSP
![[Pasted image 20260521182124.png]]
![[Pasted image 20260521182223.png]]
