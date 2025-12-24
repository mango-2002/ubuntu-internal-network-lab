

# Ubuntu Network Lab

This is a small lab I built in VirtualBox to help me learn the basics of IT infrastructure.  
I set up an Ubuntu Server VM and an Ubuntu Client VM on a private internal network.  
The goal was for the server to give the client an IP address and handle DNS name lookups. 

## What I built

- A private internal network called **intnet**
- An **Ubuntu Server** acting as both:
  - DHCP server → automatically gives IP addresses to devices
  - DNS server → lets computers reach each other by name instead of IP
- An **Ubuntu Client** that gets its network settings from the server

## Network Details

| Device | Role | IP | How it’s assigned |
|--------|------|----|----------------|
| Server (mango.lab.local) | DHCP + DNS | 10.0.0.10 | Static |
| Client (peanut.lab.local) | Workstation | 10.0.0.50 | DHCP |

DHCP scope: `10.0.0.50 - 10.0.0.100`  
Domain name: `lab.local`

## What I learned

- Setting static IPs on Linux using Netplan
- Editing configuration files with `nano`
- How DHCP assigns IPs automatically to clients
- How DNS resolves names (ex: `ping mango.lab.local`)
- Restarting and checking services with `systemctl`
- Basic network testing with `ping` and `ip a`

## How I tested everything

✔ Client got an IP from DHCP  
✔ Client could ping the server by **IP**  
✔ Client could ping the server by **hostname**  
✔ DNS name `mango.lab.local` worked correctly  

Example output from the client:
### DHCP Test (Client)
The client automatically received an IP address by DHCP (10.0.0.50):
<img width="864" height="358" alt="dhcp" src="https://github.com/user-attachments/assets/10ac6fee-cfc0-4256-abae-352153b09f6c" />


### DNS Test (Client)
The client can resolve the server hostname using internal DNS:

<img width="891" height="293" alt="dns" src="https://github.com/user-attachments/assets/451cbf4a-28c4-4192-9f91-5036b614ff80" />


## Why I built this

I wanted to get hands-on practice with real infrastructure instead of just reading about it.

## What I want to add next

- A Windows PC joined to the network
- Active Directory + Group Policy
- Centralized logging or monitoring

---

This is my first home lab, but I already learned a ton doing it ^.^ 
