Markiyan Ferendovych 4CS-31

```
vagrant up – запустити VM
vagrant reload – перезапустити VM і застосувати зміни
vagrant ssh – підключитися до VM по SSH
lsblk – показати список дисків і розділів
sudo pvcreate – створити фізичний том LVM
sudo vgcreate – створити групу томів LVM
sudo lvcreate -L 800M -n vol0 vg1 – створити логічний том vol0
sudo mkfs.ext4 /dev/vg1/vol0 – відформатувати том vol0 в ext4.
sudo mkdir -p /mnt/vol0 /mnt/vol0 – створити точки монтування
df -h – показати використання диску
sudo vgdisplay – показати інформацію про групи томів
sudo lvdisplay – показати інформацію про логічні томи
```