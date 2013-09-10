rasp-ready
==========

A code repository for provisioning my Raspberry Pis.

Installing Raspbian to the card (on Mac OS X):

    $ curl -L -O http://downloads.raspberrypi.org/raspbian_latest
    $ unzip raspbian_latest
    $ diskutil list # Find the corresponding disk.
    $ diskutil unmountDisk /dev/disk1
    $ sudo dd bs=1m if=`ls *raspbian.img` of=/dev/disk1
    $ diskutil eject /dev/disk1

Perform initial setup:

    $ ssh pi@raspberry
    $ sudo raspi-config
    $ sudo apt-get update

For web display (need to enable boot to desktop with `raspi-config`):

    $ sudo apt-get -y install ttf-mscorefonts-installer unclutter
    $ sudo ex /etc/lightdm/lightdm.conf <<INPUT
    /SeatDefaults
    :a
    xserver-command=X -s 0 dpms
    .
    :x
    INPUT
    $ sudo ex /etc/xdg/lxsession/LXDE/autostart <<INPUT
    :%d
    :i
    @xset s off
    @xset -dpms
    @xset s noblank
    @midori -e Fullscreen -a http://google.com
    .
    :x
    INPUT
