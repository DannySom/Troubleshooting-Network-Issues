# Troubleshooting Network Issues
<p align="center">
<img width="1310" height="873" alt="image" src="https://github.com/user-attachments/assets/1e90c9c4-f987-446f-a19e-00c24567e00a" />
</p>

<h1>Network Connectivity</h1>
This is a quick and simple repository to reference whenever you come across network issues in the real world. It will cover the most common issues you may encounter in classrooms, offices, workplaces, etc.

<h2>🌐 Limited Connectivity</h2>

Possible Causes or Root Issues:
Common causes include incorrect IP configurations, network hardware issues, or a disruption in the communication path. Identifying where the connection is failing is key to resolving the problem.
<ins>Fixes:</ins>

1.) Check for an APIPA address by going into the command prompt and typing `ipconfig.` If you see 169.254.x.x, then you will need to resolve that by going to the next issue which goes deep into resolving APIPA.
   - An APIPA address occurs when a device cannot obtain an IP address from the DHCP server, resulting in a self-assigned address in the range of 169.254.x.x.

2.) Ping your Local Gateway (e.g., ping 192.168.1.1)
   - Pinging the local gateway tests connectivity to the first hop on the network, which is usually the router. If the ping fails, the issue is likely with your connection to the router.
   - If it is an issue with the connection to your router, check things such as a faulty cable, a disabled network adapter, Wi-Fi configuration issues, or a malfunctioning router port.

```bash
ping [gateway IP]
```

3.) Ping a public DNS server and ping a domain name.
   - If pinging the public IP works but the domain fails, the issue may lie with DNS settings. Reconfigure DNS to use a public server like Google DNS
```bash
ping 8.8.8.8
```
```bash
ping www.google.com
```


4.) Restart network devices.

<h2>🌐 APIPA / No Valid IP Address (169.254.x.x)</h2>

Possible Causes or Root Issues:
DHCP server unavailable or unreachable, network cable unplugged or faulty, wireless connection issues, disabled or malfunctioning network adapter, or router/modem failure.

<ins>Fixes:</ins>

1.) Verify the network connection.
   - Ensure the Ethernet cable is securely connected or that the system is connected to the correct Wi-Fi network.
   - Try a different cable or network port if available.

2.) Check the assigned IP address. Open Command Prompt and run:
```bash
ipconfig
```
   - If the IP address begins with 169.254.x.x, the system failed to obtain an address from DHCP.

3.) To force the system to request a new IP address from the DHCP server, go to Command Prompt and run:
```bash
ipconfig /release
```
```bash
ipconfig /renew
```


4.) Restart network devices.


5.) Check the network adapter status.
   - Open Device Manager and ensure the network adapter is enabled.
   - Update or reinstall the network adapter driver if necessary.


6.) To Verify DHCP is enabled, open the network adapter’s IPv4 settings and confirm that Obtain an IP address automatically is selected.
   - Press ```Win + R``` and type ```ncpa.cpl```
   - Right-click your active network adapter and select properties
   - Double-click Internet Protocol Version 4 and ensure that "Obtain an IP address automatically" is enabled


7.) If the issue persists, test the connection on another device.
   - If multiple devices receive APIPA addresses, the issue is likely with the router or DHCP service.


<h2>🌐 DNS Resolution Issues</h2>

Possible Causes or Root Issues:
Incorrect or unreachable DNS servers, DNS cache corruption, network connectivity issues, router or ISP DNS outages, misconfigured network settings, or firewall/security software interference.

<ins>Fixes:</ins>

1.) Test connectivity by running:
```bash
ping 8.8.8.8
```
   - If this fails, troubleshoot general network connectivity before continuing.

2.) Test DNS resolution.
   - Attempt to access a website by name (e.g., www.google.com).
   - If the site fails to load but IP-based pings succeed, the issue is likely DNS-related.

3.) Use nslookup to test DNS functionality. Open Command Prompt and run:
```bash
nslookup www.google.com
```

   - If the command fails or times out, DNS resolution is not functioning properly.

4.) Flush the DNS cache. Open Command Prompt as administrator and run:
```bash
ipconfig /flushdns
```
This clears cached or corrupted DNS entries.

5.) Renew the IP address. Run the following commands:
```bash
ipconfig /release
```
```bash
ipconfig /renew
```
This refreshes network configuration and DNS server assignments.

6.) Check DNS server settings.
   - Open the network adapter’s IPv4 settings.
   - Ensure Obtain DNS server address automatically is selected, or verify that correct DNS servers are entered.

Common public DNS servers include:

8.8.8.8

8.8.4.4

7.) Restart network devices.

Restart the computer.

Power cycle the modem and router to refresh DNS services.

8.) Temporarily disable firewall or security software for testing.

Some security software may block DNS traffic.

Re-enable protection after testing.


7.) If the issue persists, test the connection on another device.
   - If multiple devices receive APIPA addresses, the issue is likely with the router or DHCP service.
