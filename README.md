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
