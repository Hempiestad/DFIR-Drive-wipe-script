ZERODRIVE (Windows)
format DRIVE_LETTER: /FS:filesystem /P:passes
the zerodrive script starts with the format command. The format command is followed by the drive letter of the drive you desire to write all zeros to.
adding the command /FS next allows you to choose a files system to be added to the drive. the options are:

NTFS- This is the most common file system used in modern Windows operating systems. It supports large file sizes, file compression, and encryption.
FAT32 - FAT32 is an older file system that is compatible with a wide range of devices and operating systems. It has limitations on file size and volume size compared to NTFS.
exFAT - exFAT is designed to overcome some of the limitations of FAT32, such as maximum file size and volume size. It is suitable for flash drives and external storage devices.
ReFS - ReFS is a newer file system introduced by Microsoft. It is designed for high resiliency and reliability, especially in environments with large volumes and critical data.
UDF -UDF is a file system standard used for optical media such as DVDs and Blu-ray discs. It is also used for some USB flash drives.

The command /P indicates the number of passes 
/P:0: Performs a quick format without overwriting any data.
/P:1: Writes zeros to every sector once. This is a basic level of data wiping.
/P:n (where n is greater than 1): Performs multiple passes, overwriting the disk sectors with different patterns each time. The more passes, the more secure the data wiping process is considered. However, it also takes longer to complete.
For most ordinary formatting needs, you may not need to specify /P as it defaults to 0 (quick format). However, if you're formatting a drive with sensitive data and want to ensure that it's difficult to recover, specifying /P with a value greater than 0 is recommended.

An example of the script being used to wipe a drive indicated as G with the NTFS filesystem would be 
format G /FS:NTFS /P:1

ZERODRIVE-LINUX
dd if=/dev/zero of=/dev/sdX bs=1M

Replace /dev/sdX with the actual name of the drive you want to format. caution is advised with this command, as it will irreversibly erase all data on the specified drive.

Explanation of the command:

if=/dev/zero: Specifies the input file. /dev/zero is a special file that provides as many null characters (zeroes) as you read from it.
of=/dev/sdX: Specifies the output file (the drive you want to format).
bs=1M: Sets the block size to 1 megabyte. You can adjust this value according to your needs.

More detail on block size selection choices below

***Make sure you have the correct device name (/dev/sdX). If you specify the wrong device, you can end up erasing important data***

Remember to run this command with superuser privileges (using sudo) to ensure proper access to the drive.

In the context of formatting a drive with zeros using the dd command in Unix-like systems, the block size (bs) parameter specifies the amount of data that dd reads from or writes to the input or output file at a time. The significance of the block size lies in its impact on the efficiency and performance of the data transfer process.

Here's why the block size is significant:

Performance: Choosing an appropriate block size can significantly affect the speed of the data transfer. A larger block size can reduce the number of individual read and write operations, leading to faster overall transfer speeds, especially when dealing with large files or drives.

Memory Usage: Larger block sizes may require more memory to process, as dd needs to buffer the data being transferred. However, excessively large block sizes can also lead to inefficient memory usage, particularly if the system has limited resources.

I/O Operations: The block size can influence the number of I/O operations performed by the system. Smaller block sizes result in more frequent I/O operations but may be necessary for tasks requiring fine-grained control or compatibility with certain devices.

Here are some common block size options you might encounter:

Bytes: You can specify the block size in bytes, such as bs=512 for a block size of 512 bytes.
Kilobytes (KB): You can specify the block size in kilobytes by appending 'k' to the value, such as bs=1k for a block size of 1 kilobyte.
Megabytes (MB): Similarly, you can specify the block size in megabytes by appending 'M' to the value, such as bs=1M for a block size of 1 megabyte.
Gigabytes (GB): For even larger block sizes, you can use 'G' to specify gigabytes, such as bs=1G for a block size of 1 gigabyte.
The choice of block size depends on factors such as the nature of the data, the capabilities of the underlying hardware, and the desired balance between performance and memory usage. 



