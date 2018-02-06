#!/bin/bash

cd /tmp

echo "We are going to create a data block from dev/zero that will read from dev and output into the 32MN file."

dd if=/dev/zero of=./32MB.img bs=1M count=32

hexdump ./32MB.img | less

sleep 3s

echo "Now we create a filesystem using the mkfs command, which can create many different kinds of file systems."

mkfs -t ext4 ./32MB.img

ls -l /sbin/mkfs.*

echo "now we are going to create a mountpoint with the mount ./32MB.img/tmp command. You need to know the filesystem's device, filesystem type, and the mountpoint fer this"
 
sleep 3s

sudo mkdir /mnt/tmp

sudo mount ./32MB.img /mnt/tmp

mount
echo " the df command lets you  see information about the mounted filesystem. The numbers mean the filesystem, 1024 blocks capacity, the amount of used blocks, how many are available and the mount point."

df -h
echo  "lsblk will tell you more information about all available block devices."
sleep 3s

lsblk
sleep 3

cd /mnt/tmp

ls 

sleep 2s
echo "I dont have permission to write a txt file into this folder."

echo "Waddup my peeps?!" > hello.txt

umount /mnt/tmp

cd /tmp

hexdump -c ./32MB.img | less 

sleep 5s
echo "now we are going to create some files and make a hard link to another location. When we do a  ls -i, -i being a look at the inodes, if I were to rmdir dir_1 it wouuld not remove  remove the inode because it still points to dir_2/file_5 "
cd /tmp

mkdir dir_1 dir_2
echo "a" > dir_1/file_1
echo "b" > dir_1/file_2
echo "c" > dir_1/file_3
echo "d" > dir_2/file_4
ln dir_1/file_3 dir_2/file_5
ls -i


