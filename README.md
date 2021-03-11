# Preparing disc to boot the runtime

Download a compatible image for you devive

Write the image on the storage of your with the [Raspberry Pi Imager](https://www.raspberrypi.org/software/)

Mount the storage and change the hostname on the second partition of the image

    HOSTNAME=mica
    echo "$HOSTNAME" > <MOUNTPOINT>/runtime/fs/etc/hostname

Optionally you can fixate the MAC of the device on second partition of the image

    MAC=00:00:00:00:00:00
    mkdir <MOUNTPOINT>/runtime/fs/etc/systemd/network
    cat > <MOUNTPOINT>/runtime/fs/etc/systemd/network/00-eth0.network <<EOF
    [Match]
    Name=eth0

    [Link]
    MACAddress=$MAC

    [Network]
    DHCP=yes
    LLMNR=yes
    MulticastDNS=yes
    EOF
