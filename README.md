<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Azure Virtual Machines
- Configure Network Security Groups
- Install Wireshark on Windows VM
- Observe/Analyze Network Traffic Using Wireshark

<h2>Actions and Observations</h2>

<h3>Create Resources</h3>

- <b>Create a Windows 10 Virtual Machine (VM) in the Resource Group, including a new Virtual Network (Vnet) and Subnet</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/f671762b-f9d6-4198-898b-3f8b31007670)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/402ab76c-adc5-49f7-9d3a-8ddab0465e45)
<br />

- <b>Create a Linux (Ubuntu) VM in the same Resource Group and Vnet</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/7a614c83-ca4a-4356-89f4-ece22fe19ba2)


![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/8092d359-8b6e-4334-91fd-733e186c5c19)
<br />

<h3>Observe Network Traffic</h3>

- <b>Use Remote Desktop to connect to the Windows 10 VM</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/ec9a2782-8350-4779-b8a3-21a5761c8752)
<br />
- <b>Install Wireshark on the Windows 10 VM</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/29bb68cb-fa85-429e-9c9d-222898e64ec5)

- <b>Filter Wireshark for ICMP traffic</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/97ac126b-d1e8-4e0f-91e4-705923503bda)

- <b>Initiate a perpetual ping From Windows 10 VM to Ubuntu VM and Observe Traffic</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/e1c3baaf-6761-4975-8a7b-52b687c9526f)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/67c5b158-8b7d-40c5-971f-418a6d513adf)

- <b>Disable incoming ICMP traffic in the Network Security Group of Ubuntu VM</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/922246f1-e50f-48e8-a94c-6442b17b5d46)

- <b>Observe ICMP traffic in Wireshark and ping activity on Windows 10 VM</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/f64452b4-3209-49c3-9027-5815652bb782)

- <b>Re-enable ICMP traffic in the Network Security Group and observe traffic</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/90508825-452c-4f8f-8dd2-5525c36965d8)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/ca7af4be-c8f7-4e8e-b605-4cbd7d162e18)

- <b>Stop ping activity</b>
<br />
<h3>Observe SSH, DHCP, DNS, RDP Traffic</h3>

- <b>SSH into the Ubuntu VM from the Windows 10 VM and observe SSH traffic</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/f83807d6-795d-4a28-af3a-826c54fd0b77)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/44d1156f-4c73-42af-8556-39c0c8d080d8)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/17ba8a2b-2efe-486c-b617-6862c61e5ccc)

- <b>Attempt to renew IP address on Windows 10 VM and observe DHCP traffic(ipconfig/renew)</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/ec0b0708-04d1-4a1c-9991-a3f5d23ebfb6)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/84d4ffea-18b1-41e5-ad95-eebbfa580f29)

- <b>Use nslookup to query DNS information from Windows 10 VM and observe DNS traffic(nslookup "type in website")</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/91f9cdc4-90f2-427b-87da-20cb0774ed97)

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/3a02c5f4-2585-4a50-8ecc-a17b3f1c7a11)

- <b>Filter for RDP(or type tcp.port==3389 if no packets display) traffic and observe constant traffic due to Current Remote Desktop Connection</b>

![image](https://github.com/Postmoedev/azure-network-protocols/assets/150564271/a033a5cd-bd7c-410c-bcc9-6333497c8f56)

<h3>Reminder:Make sure to delete the Resource Groups used for the lab and ensure their deletion to prevent ongoing charges for the resources!</h3>
