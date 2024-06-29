# Project: Analyzing Linux File Systems and Recovering Deleted Files

## Introduction
Linux file systems hold valuable information that can be crucial during forensic investigations. This project will guide you through the process of analyzing Linux file systems and recovering deleted files. You will learn how to use various tools and techniques to examine file system structures, identify important artifacts, and recover lost data.

## Objective
The objective of this project is to provide hands-on experience in analyzing Linux file systems and recovering deleted files. By the end of this project, you will be able to effectively use forensic tools to examine file systems and recover deleted data.

## Lab Setup and Tools
To complete this project, you will need access to a Linux operating system. You can use a physical machine, set up a virtual machine using software like VirtualBox or VMware, or use a cloud-based Linux instance.

### Pre-requisites
- Basic understanding of Linux OS and command-line interface
- Administrative privileges on the Linux machine

### Tools Installation
For this project, we will use the following tools:
1. **TestDisk**: A powerful data recovery software.
2. **Extundelete**: A utility to recover deleted files from ext3/ext4 partitions.
3. **Sleuth Kit (TSK)**: A collection of command-line tools for digital forensics.

#### Installing TestDisk
1. Install TestDisk using the package manager:
    ```bash
    sudo apt-get install testdisk
    ```

#### Installing Extundelete
1. Install Extundelete using the package manager:
    ```bash
    sudo apt-get install extundelete
    ```

#### Installing Sleuth Kit (TSK)
1. Install Sleuth Kit using the package manager:
    ```bash
    sudo apt-get install sleuthkit
    ```

## Exercises

### Exercise 1: Examining File System Structure with Sleuth Kit
**Objective**: Learn how to examine the file system structure using Sleuth Kit tools.

**Steps**:
1. Open a terminal.
2. Identify the partition you want to examine:
    ```bash
    sudo fdisk -l
    ```
3. Use `fsstat` to display the file system details:
    ```bash
    sudo fsstat /dev/sdX1
    ```
4. Use `fls` to list the files and directories in the partition:
    ```bash
    sudo fls -r /dev/sdX1
    ```

**Expected Output**: You should be able to view the file system structure and details of the specified partition.

### Exercise 2: Recovering Deleted Files with TestDisk
**Objective**: Use TestDisk to recover deleted files from a Linux file system.

**Steps**:
1. Open a terminal.
2. Start TestDisk:
    ```bash
    sudo testdisk
    ```
3. Follow the on-screen instructions to select the disk and partition you want to recover files from.
4. Choose the option to list files and navigate to the directory containing deleted files.
5. Select the deleted files you want to recover and copy them to a safe location.

**Expected Output**: You should be able to recover deleted files and save them to your specified location.

### Exercise 3: Recovering Deleted Files with Extundelete
**Objective**: Use Extundelete to recover deleted files from ext3/ext4 partitions.

**Steps**:
1. Open a terminal.
2. Identify the partition you want to recover files from:
    ```bash
    sudo fdisk -l
    ```
3. Unmount the partition (if it is mounted):
    ```bash
    sudo umount /dev/sdX1
    ```
4. Use Extundelete to recover deleted files:
    ```bash
    sudo extundelete /dev/sdX1 --restore-all
    ```
5. Check the output directory (usually `RECOVERED_FILES`) for the recovered files.

**Expected Output**: You should be able to recover deleted files from ext3/ext4 partitions and find them in the output directory.

### Exercise 4: Analyzing Metadata with Sleuth Kit
**Objective**: Use Sleuth Kit to analyze file metadata and understand file system changes.

**Steps**:
1. Open a terminal.
2. Use `istat` to display detailed metadata of a specific file:
    ```bash
    sudo istat /dev/sdX1 <inode_number>
    ```
3. Use `icat` to extract the content of a specific file:
    ```bash
    sudo icat /dev/sdX1 <inode_number> > recovered_file
    ```

**Expected Output**: You should be able to view and analyze file metadata, and extract file content using Sleuth Kit tools.

### Exercise 5: Creating and Analyzing Disk Images
**Objective**: Learn how to create and analyze disk images for forensic investigations.

**Steps**:
1. Open a terminal.
2. Use `dd` to create a disk image of a partition:
    ```bash
    sudo dd if=/dev/sdX1 of=disk_image.dd bs=4M
    ```
3. Use `mmls` from Sleuth Kit to display the partition layout of the disk image:
    ```bash
    sudo mmls disk_image.dd
    ```
4. Mount the disk image as a loop device and analyze its contents:
    ```bash
    sudo mount -o loop,ro disk_image.dd /mnt
    cd /mnt
    ls -l
    ```

**Expected Output**: You should be able to create a disk image and analyze its contents, identifying key file system artifacts.

---

With these exercises, you will gain practical experience in analyzing Linux file systems and recovering deleted files. This will enhance your skills in digital forensics and help you effectively investigate and recover valuable data from Linux systems.
