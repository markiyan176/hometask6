Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"

config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end
  
  (1..4).each do |i|
    config.vm.disk :disk, size: "400MB", name: "disk#{i}"
  end
  config.vm.provision "shell", inline: <<-SHELL
    for disk in /dev/sd{b,c,d,e}; do
      parted --script $disk mklabel gpt
      parted --script $disk mkpart primary 0% 100%
    done

    pvcreate /dev/sd{b,c,d,e}1
    vgcreate vg1 /dev/sd{b,c,d,e}1

    lvcreate -L 790M -n vol0 vg1
    lvcreate -L 790M -n vol1 vg1

    mkfs.ext4 /dev/vg1/vol0
    mkfs.ext4 /dev/vg1/vol1

    mkdir -p /mnt/vol0 /mnt/vol1

    mount /dev/vg1/vol0 /mnt/vol0
    mount /dev/vg1/vol1 /mnt/vol1

    echo "/dev/vg1/vol0 /mnt/vol0 ext4 defaults 0 0" >> /etc/fstab
    echo "/dev/vg1/vol1 /mnt/vol1 ext4 defaults 0 0" >> /etc/fstab
  SHELL
end
