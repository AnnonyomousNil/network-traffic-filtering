# network-traffic-filtering
**TASK 2** 
Linux Firewall Configuration using UFW

Every year, millions of systems and devices are vulnerable to cyber attacks. If suspicious network traffic is monitored and stopped beforehand, then most of these threats can be avoided.

A **firewall** can be either hardware, software, or both. It monitors **incoming and outgoing network traffic** based on **predefined rules**, acting like a digital shield that controls what enters and exits your system.

In this guide, we will walk through how to configure **Uncomplicated Firewall (UFW)** on Linux systems.

---

## Step 1: Check if UFW is Installed

Open your terminal and type:

```bash
ufw status
```

If UFW is not installed, it will prompt you to install it.



## Step 2: Enable UFW

To activate the firewall, run:

```bash
sudo ufw enable
```

You should see:
"Firewall is active and enabled on system startup"



## Step 3: Block Telnet Service (Port 23)
We will test the firewall by blocking telnet service.
To block all inbound traffic from port 23:

```bash
sudo ufw deny 23
```

We can check if the rule is added or not by:

```bash
sudo ufw status numbered
```



## Step 4: Test the Rule Using nmap

First, find your IP address:

```bash
ifconfig
```

Then scan port 23 using nmap:

```bash
sudo nmap -p 23 <IP address>
```

If the STATUS shows **filtered**, that means the firewall rule is working as expected.



## Step 5: Re-Allow Port 23

To allow port 23 traffic again:

```bash
sudo ufw allow 23
```

Scan again with nmap, and it should show:

```bash
PORT   STATE  SERVICE
23/tcp closed telnet
```

This means it’s no longer filtered, but the service is not open.



## Step 6: Allow SSH (Port 22)
Now we will allow ssh service to run through the firewall.
To allow SSH access through the firewall:

```bash
sudo ufw allow 22
```

All rules can again be seen by doing:

```bash
sudo ufw status numbered
```



## Step 9: Reset UFW
We will close it all off by removing all the UFW rules that were added.
To remove all UFW rules and reset the firewall we will do:

```bash
sudo ufw reset
```

---

## Conclusion

Firewalls are a critical part of your system’s defense. Using UFW on Linux makes it simple to manage your firewall and protect your system from unwanted traffic.
