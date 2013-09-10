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

