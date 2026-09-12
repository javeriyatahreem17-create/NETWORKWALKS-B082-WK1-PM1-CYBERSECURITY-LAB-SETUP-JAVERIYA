# NETWORKWALKS-B082-WK1-PM1-CYBERSECURITY-LAB-SETUP-JAVERIYA
# 🔐 Cybersecurity Lab Environment Setup
Building a virtual cybersecurity laboratory using VirtualBox and Kali Linux for hands-on security practice.

## 📌 Project Overview
This project covers the setup of a virtual cybersecurity laboratory using **Oracle VirtualBox** and **Kali Linux**.
The main goal was to create a controlled environment where I can practice networking, reconnaissance, scanning, vulnerability assessment and other cybersecurity techniques without working on unauthorized systems.

The environment can also be extended later by adding other virtual machines as controlled targets.

## 🎯 Objectives

The main objectives of this lab were:
- Install and configure Oracle VirtualBox.
- Set up Kali Linux as a virtual machine.
- Create a dedicated NAT Network.
- Configure network connectivity for Kali Linux.
- Understand and configure IPv4 settings.
- Verify IP, gateway and DNS connectivity.
- Create a clean snapshot of the configured VM.
- Build a base environment for future cybersecurity labs.

## 🛡️ Purpose of the Lab

This laboratory provides a controlled environment for learning and practicing cybersecurity concepts.

It can later be used for:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Enumeration
- Exploitation practice
- Security-tool experimentation

> ⚠️ **Ethical Use:** This environment should only be used against systems that I own or have explicit permission to test.

## 🏗️ Lab Architecture

The current laboratory consists of a Kali Linux virtual machine connected to a VirtualBox NAT Network.

Additional virtual machines can be connected to the same network later and used as intentionally configured targets for authorized security testing.

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| 🖥️ Host OS | Windows 11 |
| 🧰 Hypervisor | Oracle VirtualBox |
| 🐉 Security OS | Kali Linux 2026.2 |
| 🧠 Kali RAM | 4096 |
| 🌐 Virtual Network | NAT Network |
| 📡 Network Address | 10.0.0.0/24 |
| 🐧 Kali IP Address | 10.0.0.2/24 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |


# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package before importing it into VirtualBox. (.7z archive)

## Step 2. Install VirtualBox

Oracle VirtualBox was installed as the virtualization platform for the laboratory.

VirtualBox allows Kali Linux to run as a separate virtual machine while using the resources of the host computer.

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox for the cybersecurity lab.

The NAT Network allows multiple virtual machines to communicate with each other while also providing external network connectivity.
<img width="1913" height="1027" alt="Screenshot 2026-09-11 155606" src="https://github.com/user-attachments/assets/91a83511-fb80-43c2-a561-db62b6d095f7" />

### Network Configuration

Network Name : NATNetwork IPv4 Prefix  : 10.0.0.0/24 DHCP: Enabled IPv6: Disabled

## Step 4. Import and Configure Kali Linux

After creating the NAT Network, I imported the Kali Linux virtual machine into VirtualBox and opened its settings to connect it to the newly created network.

The Kali Linux VM was configured with the required system resources and its network adapter was attached to the `NATNetwork` created in the previous step.

### Network Adapter Configuration:

- **Adapter:** Adapter 1
- **Attached to:** NAT Network
- **Network Name:** NATNetwork

This configuration allows Kali Linux to communicate through the laboratory's virtual network while maintaining the network setup required for future cybersecurity exercises.
<img width="1910" height="1032" alt="Screenshot 2026-09-11 155708" src="https://github.com/user-attachments/assets/853cfe05-136d-4cb2-8530-b8cfbada45bc" />
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

## Step 5. Configure Kali Linux Network Settings

After starting the Kali Linux VM, I verified that the network adapter was detected correctly and checked the assigned IPv4 configuration.

The main network parameters were:
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8, 10.0.0.1
<img width="1915" height="1032" alt="Screenshot 2026-09-11 155822" src="https://github.com/user-attachments/assets/bf38cb90-0371-44f6-bfb4-e503b6db9040" />

## Step 6. Create a Clean Snapshot

After completing the Kali Linux and network configuration, I created a VirtualBox snapshot.

A snapshot saves the current state of the virtual machine and provides a recovery point before performing future experiments.

This is particularly useful in a cybersecurity lab because security tools, configurations, and experiments can sometimes change the system. If something goes wrong, the VM can be restored to the clean state instead of setting up everything again.

Snapshot Name : Freshly set kali linux
<img width="1917" height="983" alt="Screenshot 2026-09-12 132031" src="https://github.com/user-attachments/assets/f73e324f-83e8-40f1-925c-c99f6c77d1da" />

🔎 Lab Verification

After completing the setup, I performed a few basic checks to confirm that the Kali Linux environment and its network configuration were working correctly.
| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | Correct Kali IP displayed       |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution        | `nslookup networkwalks.com`     | Domain resolves                 |

🐞 Problems Encountered & Solutions:

## Problem 1: Network Connectivity Issue

During the network configuration process, connectivity problems can occur because of an incorrect IP configuration, gateway, DNS setting, or VirtualBox network adapter.

I approached the problem by checking each part of the connection separately.

First, I checked the assigned IP address:
bash:
ip a

Then I tested communication with the gateway:
bash:
ping 10.0.0.1

After that, I checked external connectivity:
bash:
ping 8.8.8.8

## Problem 2: Understanding the Network Information in Kali

When I first checked the network configuration using:

ip a

the output contained several lines and interface details that were initially confusing.

Solution

I focused on the active network interface and identified the IPv4 address assigned to Kali Linux.

I then used:

ping 10.0.0.1
and:
ping 8.8.8.8
-to understand whether the VM could communicate with the gateway and external network.
.

## 💡 What I Learned

This lab helped me connect basic networking concepts with an actual working Linux environment.

## 1. Virtualization

I learned how Oracle VirtualBox allows Kali Linux to run as a virtual machine on my computer.
This means I can create and manage different systems for cybersecurity practice without needing separate physical computers

## 2. NAT Network

I learned that creating a NAT Network is different from simply starting a virtual machine with a default network configuration.
A NAT Network can provide a common virtual network where multiple machines can later communicate with each other.
This will be useful when I add target machines for future security exercises.

## 3. IPv4 Networking

I gained practical experience with important networking concepts such as:
IP address
Subnet
Network interface
Default gateway
DNS
Using commands such as ip a and ping helped me understand how these concepts appear on a real Linux system.

## 4. Network Verification

I learned that network connectivity should be checked step-by-step.
For example, checking the IP address, testing the gateway, testing an external IP and finally checking DNS helps identify where a connectivity problem is occurring.

## 5. Snapshots and Recovery

I learned why creating a clean snapshot is useful before starting cybersecurity experiments.
If a future experiment changes the VM or causes a configuration problem, I can restore the previous working state instead of repeating the entire installation process.

🔐 Security & Ethical Use
This laboratory is intended strictly for education purposes only.


🧰 Tools & Resources

| Tool                 | Purpose                                          |
| -------------------- | ------------------------------------------------ |
| 🐧 Kali Linux        | Cybersecurity testing environment                |
| 📦 Oracle VirtualBox | Virtualization platform                          |
| 🗜️ 7-Zip            | Extracting compressed VM files                   |
| 🔍 Nmap              | Network discovery and scanning                   |
| 🌐 `ip`              | Checking network interfaces and IP configuration |
| 📡 `ping`            | Testing network connectivity                     |
| 🔎 `nslookup`        | Testing DNS resolution                           |


## Useful Resources
Kali Linux: https://kali.org/get-kali

Oracle VirtualBox: https://virtualbox.org/wiki/Downloads

7-Zip: https://7-zip.org/download.html

## ✍️ Author
Waqas Karim

## 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
