# Pre-Security - 5. OS , Linux and  Windows CLI Basics

## **1. Operating System**

An **operating system** (OS) is the core software that coordinates everything happening on a computer. It sits between the user, applications, and the system’s physical hardware, acting as the invisible manager that keeps the entire machine running as one unified system.

- Your **hardware** (storage, connected devices): The runways, airplanes, fuel systems, radar, and other physical infrastructure.
- Your **applications** (web browser, game launcher): The various airlines and their passengers, all trying to take off, land, and request services.
- Your **operating system** (Windows, , macOS): The entire air traffic control system, directing all of this activity. It schedules resources, manages traffic, resolves conflicts, and ensures safety.

**System Privilege Layers:** 

Inside a modern computer, different parts of the system operate at various permission levels. Some components can communicate directly with the hardware, while regular applications run in a safer, restricted environment. This separation is intentional and helps prevent conflicts and security issues.

- **Kernel space**: The privileged, locked-down core of the . This is where the kernel, the part of the operating system that directly manages hardware and system resources, runs. It has unrestricted access to the , memory, storage, and all hardware components.
- **User space**: Where all standard applications run. Applications in the user space are deliberately prevented from accessing hardware directly. Whenever they need to open or save a file, play a sound, or connect to Wi-Fi, they must make a system call and request that the kernel act on their behalf.

| **OS Responsibility** | **What the OS Does** | **Example** |
| --- | --- | --- |
| Process Management | Creates, schedules, prioritizes, and terminates running programs. The OS decides how much CPU time each process gets, making multitasking feel seamless | Opening multiple apps, like your browser, music player, and social media, without your computer freezing |
| Memory Management | Allocates RAM to processes, protects the app's memory from other processes, and reclaims memory when apps are closed. When RAM runs low, the OS uses virtual memory to keep your system stable | Opening multiple app at once, the OS allocates RAM to each one and keeps them isolated so they don’t interfere or crash each other |
| File System Management | Organizes files into directories, handles naming, paths, permissions, metadata (name, size, type, timestamps) | Creating a new folder, saving a photo, or setting a file to "read only" |
| User Management | Handles multiple user accounts, authentication, and permissions to determine who can access what | Logging in with your password and keeping your files inaccessible to other user accounts |
| Device Management | Loads drivers and provides a universal interface (hardware abstraction layer), so apps can say “print this” or “play this sound” | Plugging in a new mouse, printer, or external hard drive and having it work immediately |

Which OS space has unrestricted access to your computer's hardware? Kernel Space

Which OS responsibility manages user accounts, authentication, and permissions? User Management

## **2. OS Interfaces**

Interaction with the OS can be divided into two main parts: the **graphical user interface** (GUI) and the **command-line interface** (CLI).

**Graphical User Interface:** A **GUI** allows users to interact with a computer through visual elements like **icons, windows, menus, and buttons**. It is user-friendly and does not require memorizing commands.

**Command-line Interface:** A **CLI** allows users to control a computer by typing **text-based commands**. It provides more **precision, speed, and control** for advanced tasks but requires knowledge of the correct commands and syntax.

| **Operating System Type** | **Primary Use Case** | **Key Characteristics** |
| --- | --- | --- |
| Desktop | Personal computers, daily work, gaming, content creation | Rich graphic interface, runs many apps at once, user-focused |
| Server | Web hosting, databases, cloud services, back-end | Headless (no GUI), maximum uptime, multi-user, remote access |
| Mobile | Smartphones and tablets | Touch-based UI, power efficient, always connected, app sandboxing |
| Embedded | Appliances, cars, IoT devices, smart TVs, routers | Tiny footprint, runs on limited hardware |
| Virtual/Cloud | Virtual machines, containers, cloud instances | Lightweight, scalable, rapid deployment |

Keeping your OS secure is essential for protecting data and privacy:

✔️ Keep the OS updated

✔️ Use strong, unique passwords

✔️ Create standard user accounts

✔️ Install trusted security software

✔️ Enable a firewall

✔️ Secure network connections

✔️ Disable unnecessary services

✔️ Manage application permissions

✔️ Encrypt storage drives

✔️ Use backups and restore points

✔️ Monitor suspicious activity

✔️ Continue learning about cybersecurity

## **3. Linux CLI Basics**

Linux OS using the **command-line interface (CLI).** The **terminal** is a text-based interface for controlling a Linux system. 

1. PWD Command: Where Am I?

```bash
ubuntu@tryhackme:~$ pwd
/home/ubuntu
```

 2. ls Command: What's Around Me? , ls -l with more details, ls -al hidden files

```bash
ubuntu@tryhackme:~$ ls
Desktop    Downloads  Pictures  Templates  logs
Documents  Music      Public    Videos     projects
```

```bash
ubuntu@tryhackme:~$ ls -al
total 144
drwxr-xr-x 24 ubuntu ubuntu  4096 Feb 10 10:48 .
drwxr-xr-x  3 root   root    4096 Feb 10 10:36 ..
-rw-------  1 ubuntu ubuntu   439 Feb 10 06:47 .Xauthority
```

1. cd Command: Move Around

```bash
ubuntu@tryhackme:~$ cd Documents/
ubuntu@tryhackme:~/Documents$ pwd
/home/ubuntu/Documents
```

1. find Command: used to locate files within the file system

```bash
ubuntu@tryhackme:~$ find ~ -name mission_brief.txt
/<REDACTED-PATH>/mission_brief.txt
```

1. cat Command: ****Read the File

```bash
ubuntu@tryhackme:~/<REDACTED-PATH>$ cat mission_brief.txt
Great job finding your way around the terminal.
```

1. whoami Command: Who Are You Logged in As?

```bash
ubuntu@tryhackme:~$ whoami
ubuntu
```

1. uname -a Command: To see details about the operating system, kernel version, and architecture,

```bash
ubuntu@tryhackme:~$ uname -a
Linux tryhackme <REDACTED>-aws #17-Ubuntu SMP Mon Sep  2 13:48:07 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

1. df -h Command:  tools or analyzing logs

```bash
ubuntu@tryhackme:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        --G   12G   --G  17% /
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           774M  1.2M  773M   1% /run
```

## **4. Windows CLI Basics**

The **Command Prompt** (often referred to as CMD) is a text-based interface for interacting with the Windows operating system. Instead of clicking folders and menus, you type commands to tell the system exactly what you want to do, such as listing files, moving between folders, or checking system information. 

**Step 1: Where Am I?** Before doing anything else, open the terminal on the Desktop, and check your current location by typing the command `cd`, 

**Step 2: What's Around Me?** Now, list the contents of the current directory using the command: `dir`

**Step 3: Are There Hidden Files?** Some files and folders on Windows are marked as hidden, which means they don't appear in a normal listing. To show everything, including hidden items, run: `dir /a`

**Step 4: Moving Around the Filesystem!** Let's use the `cd` command to navigate through the folders. We can use the format `cd folder_name` to move to the specified folder.

**Step 5: Finding the File on the Disk** Instead of guessing where the file is, let Windows search for it. Use the following command: `dir /s task_brief.txt`. The `/s` flag tells Windows to search **all subfolders** starting from your current directory

**Step 6: Navigate to the File** Now that we know where the file is located, let's use the cd command to navigate to the folder using the command format `cd <path_to_the task_brief.txt>`. Use `dir` again to confirm that **task_brief.txt** is in the folder

**Step 7: Read the File** Now read the contents of the file using: `type task_brief.txt`. This will print the contents of the file directly in the command prompt,

**Step 8: Who Am I Logged In As?** When working on a system, one of the first things to check is **which user account you’re using**. This matters because different users can have different permissions. Run the following command:`whoami`.

**Step 9: What Is the Name of This Computer?**  Every Windows machine has a name. In workplaces, this helps identify network systems. To see the computer’s name, run: `hostname`.

**Step 10: What Version of Windows Is This?** Next, let’s look at details about the operating system itself. Run:`systeminfo`

**Step 11: How Is This Machine Connected to the Network?**  Finally, let’s look at basic network information. Run: `ipconfig`