Q: An administrator is comparing legacy and modern storage controllers for a Linux server. According to Linux storage basics, which of the following accurately describes the hardware connection interfaces?
A) PATA uses a serial interface and supports up to 4 devices, while SCSI uses a parallel interface supporting up to 8 devices.
B) SATA uses a serial interface supporting up to 4 devices, while PATA uses a parallel interface supporting up to 2 devices.
C) SCSI uses a serial interface supporting up to 8 devices, while SATA uses a parallel interface supporting 4 devices.
D) PATA and SATA both use parallel interfaces, but SATA supports up to 8 devices per adapter.

A: B - SATA (Serial Advanced Technology Attachment) connects drives using a serial interface and supports up to four devices per adapter, whereas PATA (Parallel Advanced Technology Attachment) uses a parallel interface and supports only two devices per adapter. SCSI connects using a parallel interface, not serial, and supports up to eight devices.

---

Q: You are installing a lightweight Linux OS on an embedded device that uses a MicroSD card as its primary boot drive. What naming convention will the Linux kernel use to represent the second partition of this storage device in the `/dev` directory?
A) `/dev/sdb2`
B) `/dev/mmcblk0p2`
C) `/dev/nvme0n1p2`
D) `/dev/sdcard0p2`

A: B - The exception to the standard `sd` prefix pattern occurs with memory cards (SD cards) and NVMe devices. For SD cards, the path `/dev/mmcblk0p1` represents the first partition, making `/dev/mmcblk0p2` the correct identifier for the second partition. Option C is for an NVMe SSD, and Option A is for a secondary SATA/SCSI drive.

---

Q: A senior technician attaches a legacy IDE hard drive as the slave device on the primary IDE channel. Simultaneously, they connect a new SATA drive as the first device on the SATA controller. How will the Linux kernel represent the raw block devices for the IDE slave and the SATA drive, respectively?
A) `/dev/sdb` and `/dev/sda`
B) `/dev/hda2` and `/dev/sdb`
C) `/dev/hdb` and `/dev/sda`
D) `/dev/ide0` and `/dev/sat0`

A: C - For legacy PATA/IDE devices, the file is named `/dev/hdx`, with `/dev/hda` reserved for the master on the first channel and `/dev/hdb` for the slave. SATA drives emulate SCSI naming conventions and use the `/dev/sdx` prefix, meaning the first SATA drive is represented as `/dev/sda`.

---

Q: An administrator attempts to partition a newly purchased 4 TB mechanical hard drive using the legacy Master Boot Record (MBR) scheme. Why is this partitioning scheme technically unsuitable for this specific drive?
A) MBR can only address disks up to 2 TB in size and natively supports a maximum of 4 primary partitions.
B) MBR is strictly limited to 128 primary partitions, which restricts logical addressing beyond 2 TB.
C) MBR requires a UEFI firmware interface to address drives larger than 2 TB, which requires an EFI System Partition.
D) MBR can only create 3 primary partitions and 1 extended partition, effectively capping the drive size at 2 TB per partition.

A: A - The MBR partition table scheme has a series of limitations, most notably the inability to address disks larger than 2 TB in size, as well as a strict limit of only 4 primary partitions per disk. To exceed the 2 TB limit, the GPT (GUID Partition Table) method must be used instead.

---

Q: A modern server utilizes the Unified Extensible Firmware Interface (UEFI) instead of the legacy BIOS. When setting up the storage using the GUID Partition Table (GPT) method, what is the maximum number of partitions that the standard GPT scheme can natively support on a single disk?
A) 4 primary partitions and unlimited logical partitions
B) 128 partitions
C) 256 partitions
D) Unlimited partitions

A: B - Systems that use the UEFI bootloader method pair with the more advanced GUID Partition Table (GPT) method, which supports up to 128 partitions on a single drive. This eliminates the need for primary and extended partitions entirely.

---

Q: A system administrator executes the `lsblk` command and notices a partition labeled `/dev/sda5`. Based on standard Linux partition naming conventions for MBR disks, what does the number 5 specifically signify?
A) It is the fifth primary partition on the first SATA drive.
B) It is the first extended/logical partition on the first SATA drive.
C) It is the fifth physical SCSI drive connected to the system.
D) It is an LVM logical volume residing on the primary disk.

A: B - Because MBR is limited to four primary partitions (numbered 1 through 4), any partitions created beyond that are housed within an extended partition. MBR extended partitions strictly begin numbering at 5, meaning `/dev/sda5` is the first logical partition inside the extended partition.

---

Q: You are tasked with preparing a secondary 1 TB SATA disk for a Linux system. You need to create 6 isolated storage areas on this drive. If you must use the legacy MBR partitioning scheme, what is the correct approach to achieve this layout?
A) Create 6 primary partitions sequentially.
B) Create 3 primary partitions, 1 extended partition, and 3 logical partitions within it.
C) Convert the disk to GPT since MBR fundamentally cannot support more than 4 storage areas of any type.
D) Create 4 primary partitions and map the remaining 2 partitions using the `udev` daemon.

A: B - Because MBR limits you to a maximum of 4 primary partitions, the standard workaround is to create an extended partition that acts as a container. You can create 3 primary partitions, 1 extended partition, and subdivide that extended partition into multiple logical partitions to achieve the 6 desired storage areas.

---

Q: Which background application is primarily responsible for automatically detecting new hardware, such as a hot-plugged USB drive, and dynamically assigning it a unique device file in the `/dev` directory?
A) `dbus`
B) `hald`
C) `udev`
D) `sysfs`

A: C - Most Linux systems use the `udev` application, which runs in the background to automatically detect new hardware connected to the running system and assign each device a unique device filename in the `/dev` directory.

---

Q: A junior admin complains that a custom bash script fails to mount an external USB backup drive because the drive is recognized as `/dev/sdb1` on some days and `/dev/sdc1` on others. To ensure the script reliably identifies the exact same drive every time regardless of plug-in order, which `udev` directory should the script reference?
A) `/dev/disk/by-uuid/`
B) `/dev/mapper/`
C) `/proc/partitions`
D) `/sys/block/`

A: A - To solve the problem of dynamic raw device names changing, `udev` uses the `/dev/disk` directory to create persistent symbolic links. The `/dev/disk/by-uuid/` directory links storage devices by their 128-bit universally unique identifier (UUID), ensuring the exact same drive is identified every time.

---

Q: An engineer is configuring a rack-mounted server and needs a persistent link to a storage device strictly based on the physical hardware port it is plugged into, ensuring that replacing a failed drive in the exact same slot doesn't break the mount scripts. Which `udev` symbolic link directory provides this specific capability?
A) `/dev/disk/by-id/`
B) `/dev/disk/by-path/`
C) `/dev/disk/by-label/`
D) `/dev/disk/by-uuid/`

A: B - The `udev` application creates persistent device files based on various attributes. The `/dev/disk/by-path/` directory specifically links storage devices by the physical hardware port they are connected to on the system.

---

Q: As new storage devices are cold-plugged or hot-plugged, the `udev` daemon dynamically creates device nodes in the filesystem. Where does `udev` search for the pre-defined matching rules to determine how to identify and configure these devices?
A) `/proc/udev/rules/`
B) `/etc/udev/rules.d/`
C) `/var/lib/udev/`
D) `/sys/class/block/`

A: B - As new devices are detected, `udev` searches for a matching rule in the pre-defined rules stored in the directory `/etc/udev/rules.d/`.

---

Q: A Linux system is connected to a high-end storage area network (SAN). To provide fault tolerance and increased throughput, multiple physical paths exist between the server and the storage arrays. Which command-line tool is used specifically to create the device entries for these aggregated multipath storage devices?
A) `kpartx`
B) `mdadm`
C) `pvcreate`
D) `multipathd`

A: A - In DM multipathing, `kpartx` is the specific command-line tool used for creating device entries for multipath storage devices. `multipathd` is the background monitoring process, and `mdadm` is used for software RAID.

---

Q: When utilizing the Logical Volume Manager (LVM) to pool storage space across multiple hard drives, what is the correct hierarchical order of LVM components, starting from the physical raw disk up to the usable abstract storage area?
A) Logical Volume -> Volume Group -> Physical Volume
B) Physical Volume -> Volume Group -> Logical Volume
C) Volume Group -> Physical Volume -> Logical Volume
D) Physical Volume -> Logical Volume -> Volume Group

A: B - In the LVM layout, raw partitions must first be initialized as Physical Volumes (`pvcreate`), which are then grouped together into a Volume Group (`vgcreate`), and finally, that pooled space is subdivided into usable Logical Volumes (`lvcreate`).

---

Q: After successfully configuring an LVM logical volume across three physical SCSI drives, where will the Linux kernel's device mapper create the virtual block device file representing this newly created volume?
A) `/dev/disk/by-lvm/`
B) `/sys/block/lvm/`
C) `/dev/mapper/`
D) `/proc/lvm/`

A: C - The logical volumes create virtual device entries inside the `/dev/mapper/` directory. These virtual block devices are used to intercept data and abstract physical devices into logical pools.

---

Q: A system administrator wants to set up a software RAID array that provides disk striping with distributed parity, allowing the system to recover if any single drive fails while maintaining excellent read performance. Which RAID level provides this specific feature?
A) RAID 0
B) RAID 1
C) RAID 4
D) RAID 5

A: D - RAID 5 provides disk striping with distributed parity, where a parity bit is added to the data stripe and appears across all disks so that any single failed disk can be recovered. RAID 0 lacks parity, RAID 1 is mirroring, and RAID 4 uses a dedicated parity disk instead of distributed parity.

---

Q: Instead of purchasing an expensive hardware RAID controller, an administrator decides to implement software RAID directly within the Linux operating system. Which utility is used to specify multiple partitions to be aggregated into a Linux software RAID environment?
A) `mdadm`
B) `lvm`
C) `dm-multipath`
D) `kpartx`

A: A - The `mdadm` utility allows you to specify multiple partitions to be used in any type of software RAID environment. The resulting RAID device then appears as a single device in the `/dev/mapper` directory.
