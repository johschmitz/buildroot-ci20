# Buildroot ci20

A super stripped down MIPS Creator ci20 webradio image, plug in ethernet and a
headphone to listen to webradio streams from mpd. The streaming is
automatically started through mpc in an init script.

## Introduction

[Buildroot](https://buildroot.org/) is a simple, efficient and easy-to-use tool
to generate embedded Linux systems through cross-compilation.

## ci20 config

This is a buildroot configuration optimized for MIPS Creator ci20. The kernel has
been extremely stripped down to optimize boot times without having to go to a
custom init system.

## How to build

Run the following commands from the project root folder:

    make ci20_minimal_mpd_lms_defconfig

Now run

    make

and you may consider geting a cup of tea or coffee because this can take some
time.

## How to flash to SD card

Be careful with the dd command otherwise you might overwrite some important
data! Also make sure the card is not mounted when you flash it. When the card
is plugged in the reader and ready find out the correct device, e.g.,
"/dev/sdX" and run

    sudo dd if=output/images/sdcard.img of=/dev/sdX
    sync

After flashing insert the SD card into you Raspberry and power it up.

## Login and filesystem modification

The username is "root" and the password is "ci20", ssh loggin is possible.
To protect the file system it is mounted read-only at starup.
Remount rw with

    mount -o remount,rw /

to modify.
