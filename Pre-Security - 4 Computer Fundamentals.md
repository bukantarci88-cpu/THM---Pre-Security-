# Pre-Security - 4. Computer Fundamentals

### 1. What Happens When You Press the Start Button?

![Boot Sequence Diagram](https://tryhackme-images.s3.amazonaws.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1770828785615.svg)

**Step 1: Press the Power Button:** Pressing the power button sends a signal to the **Power Supply Unit (PSU)**, allowing electricity to flow and start the computer.

**Step 2: Firmware Starts:** The computer's **firmware (UEFI/BIOS)** starts initializing hardware components and prepares the system for booting. UEFI is the modern replacement for BIOS and performs the same basic function.

**Step 3: Power-On Self Test (POST):** The **UEFI runs POST** to check that essential hardware components are present, correctly configured, and working properly. Any issues may trigger warning signals.

**Step 4: Select Boot Device:** The **UEFI checks the boot order** and selects the device containing the operating system boot files, such as a hard drive or SSD.

**Step 5: Initiate Bootloader:** The **bootloader loads the operating system into RAM** from the selected boot device. After loading, UEFI transfers control of the hardware to the operating system.

| **Computer Type** | **Screen and Keyboard** | **Main Purpose** |
| --- | --- | --- |
| Laptop | Yes | Portable everyday computing. |
| Desktop | Yes | Sustained performance at a fixed location. |
| Workstation | Yes | Precision and reliability for professional tasks. |
| Server | No | Providing services to many users over a network. |

## **2. Hypervisor (The Building Manager)**

A **hypervisor** is the core technology behind virtualization. It's the software that creates and manages virtual machines.

- Divides a physical computer into multiple virtual ones.
- Gives each virtual machine its own share of , memory, and storage.
- Keeps everything isolated and safe.
- Manages the lifecycle of virtual machines (start, stop, pause, clone, delete).

Hypervisors have two main types of implementation, each of which is used for specific scenarios, from home labs to large data centers:

- **Type 1** hypervisors run directly on the physical hardware, making them fast, efficient, and ideal for servers and professional environments.
- **Type 2** hypervisors run within an existing operating system, making them easier to install and ideal for learning, testing, or small setups.

## **3. Virtual Machines (The Apartments)**

A **Virtual Machine (VM)** is a virtual computer created by the hypervisor.

- It has its own virtual , , storage, and network.
- It can run any operating system (Windows, , etc.).
- It’s completely isolated from other VMs. This means that if one  breaks, the others continue to work.

## **4. Containers (The Rooms Inside the Apartment)**

A **container** is a lightweight, isolated environment that runs a single application and all the necessary components to support it. Instead of bringing a whole separate operating system, a container borrows the core of the existing system by running on the kernel, which is the part of an operating system that communicates with the hardware and manages resources such as memory and running programs. Because containers share this kernel, they start quickly and use fewer resources than full virtual machines, but it also means they must match the host system’s type. For example, you can’t run a Windows container on a Linux machine.

Containers behave like small, self-contained spaces because:

- They package the application and its dependencies (libraries, tools, versions).
- They share the host’s operating system, so they start almost instantly.
- They remain isolated from each other, so a misbehaving  doesn’t affect the others.
- They can run consistently on any machine, making them perfect for development, testing, and scalable deployments.

The easiest way to deploy containers in a VM is using Docker. Docker is an open-source software platform that simplifies the process of building, deploying, and running applications using containerization.

**Key Terminology**

- **Virtualization:** Enables a single physical computer to act like multiple separate computers.
- **Hypervisor:** The “manager” software that makes and runs the virtual computers.
- **Virtual Machine (VM):** A whole virtual computer inside the real one, with its own system.
- **Container:** A small, isolated box for one app that shares the same system as the host.
- **Container Images:** A pre-packed recipe/template used to create containers.
- **Network Ports:** Special numbered entry points that apps use to talk over the network.

We also concluded that the key benefits of virtualization are:

- Cost savings
- Better resource usage
- Safe testing for cyber security
- Faster deployment
- Flexibility
- Portability
- Scalability
- Centralized Management

## **5. Cloud Benefits and Characteristics**

The cloud was designed to address common problems, including limited capacity, high costs, and slow growth. The following benefits and characteristics explain how cloud computing makes applications easier to run, scale, and manage:

- **Scalability:** Easily scale up or down as your application's needs change.
- **On-demand self-service:** Create or remove servers and storage instantly, without waiting for hardware.
- **Pay only for what you use:** You are charged based on usage, not upfront costs.
- **Security:** Cloud providers protect the infrastructure with strong security measures.
- **High availability:** Applications keep running even if part of the system fails.
- **Global access:** Your application can be accessed by users anywhere in the world.

**Deployment Types of Cloud**

- **Public Cloud:** Used by startups, websites, and global apps because it is affordable, easy to scale, and requires no infrastructure management. Public cloud services are preferable for nearly every use case.
- **Private Cloud:** Used by banks, healthcare, and government organizations because it offers greater control, customization, and compliance for sensitive data.
- **Hybrid Cloud:** Used by companies like e-commerce platforms that need to keep sensitive data private while still scaling publicly during high demand.

**Cloud Service Models:**

- **Infrastructure as a Service (IaaS):** You rent basic computing resources such as virtual servers, storage, and networking. You are responsible for managing the operating system and your application, while the provider manages the physical hardware.
- **Platform as a Service (PaaS):** The cloud provider manages the infrastructure and the operating system. You focus on building, deploying, and running your application without worrying about servers.
- **Software as a Service (SaaS):** You use a complete application over the internet. The provider manages everything, and you access the software through a browser or app, for example, Gmail or Zoom.

**Major Cloud Vendors**

- **Microsoft Azure:** A strong competitor, especially in enterprise and hybrid cloud environments.
- **Google Cloud Platform (GCP):** Known for powerful data analytics, , and machine learning tools.
- **Alibaba Cloud:** A major player in Asia, offering competitive cloud services globally.
- **IBM Cloud:** Focuses on hybrid cloud and driven solutions for businesses.
- **Oracle Cloud:** Focuses on enterprise applications and databases.

What is the characteristic of cloud environments that enables you to handle an unexpected increase in access to your application? Scalability 

What is the most common type of cloud deployment used? Public Cloud

Suppose you want to deploy an application to the internet, focusing only on application development and leaving infrastructure to others. What type of cloud service is the best? PaaS

**Basic Concepts from AWS:**

- **EC2 (Virtual Computer / Server):** EC2 represents a virtual computer in the cloud. Just like a real computer, it has a CPU and memory (RAM) and can run applications. Whenever you add an EC2 instance, you are adding a computer to your environment.
- **Instance Type (for example: t2, t3, m5):** Instance types describe how powerful the virtual computer is. Some have more CPU and RAM and are therefore more expensive. You choose the Instance Type based on your needs, knowing that:
    - Bigger instances = more power + higher cost
    - Minor instances = less power + lower cost