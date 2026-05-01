## 🎯 Show and Tell Interviews / Final Exam

### My Name: Thomas Kammoe 

### My Interviewers

Add a bullet in form form: `* Last name` for each person **who interviewed you** about your self-hosted implementation. Minimum of one is required.

- `* Godwin`
- `* Tadiparthi`
- `* Patel`


### Who I Interviewed

Add a bullet in form form: `* Last name` for each person **who you interviewed** about their self-hosted implementation. Minimum of three is required.

`* Tadiparthi`
`* Godwin`
`* Patel`

### 🌟 Favorite Thing

Ice breaker - ask them what their favorite thing is. If it is not on this list add a new bullet.  
Nested bullets should be in form: `* Last name - specific detail` where specific detail is something granular like specific game, pet name, etc.


* Gaming `* Patel`, `* Tadiparthi`
* Cooking
* Hiking 
* Pet
* 3D print `* Godwin`
* Sleep `* Bhattarai`
---

### 🖥️ Host OS

Inquire which OS the software is hosted on.  If it is not on this list add a new bullet.  
Nested bullets should be in form: `* Last name - OS version` where OS version is specific to the release (not just OS name).

* Windows
* Debian
* Ubuntu `* Tadiparthi`, `* Godwin 26.04`, `* Bhattarai - 24.04`, `* Patel - 24.04`
* RedHat

---

### 💾 Software

Inquire which software they implemented.  If it is not on this list add a new bullet.  
Nested bullets should be in form: `* Last name - software version` where software version is specific to the release (not just software name).

* Unraid
* TrueNAS
* BeeGFS
* Proxmox
* Grafana `* Tadiparthi -13.0.1`, `* Godwin - 13.0.1`
* Homepage `* Patel - 1.12.3`
* Immich
* Mealie `* Bhattarai - 3.16.0`
* GitLab
* ownCloud

---

### 🧪 Live Demo

Interact with or request demonstrations of their self-hosted implementation. A minimum of two feature of the software should be demonstrated.  If an interaction / demonstration method is not on this list add a new bullet.  
Nested bullets should be in form: `* Last name - describe interaction / demonstration`

* Made Account `* Tadiparthi - created users account.` `* Bhattarai - created users accounts `
* Joined server `* Bhattarai - user viewed the page but don't have admin permission.`
* Viewed Dashboard `* Godwin - it displayed aws system usage and website monitor`, `* Patel -  he displayed different applications with their live cpu. `

---

### 🔐 Network Security

Evaluate their firewall setup - this is a mix of Network ACLs, Security Groups, and / or system firewalls, per their setup. Have them explain what ports their application requires, and show their configuration settings around protected vs open ports 
Nested bullets should be in form: `* Last name - defend what about their network security is good or bad`

* Positive notes on network security `* Tadiparthi - port 22 was allow from his home ip.`, `* Patel - allow port 3000 for his application.`
`* Godwin - allow port 3000 and 9090 for grafana. `, `* Bhattarai - allow port 22 for homeip/wright state ip, and port 9925 allow to all.`

* Negative / recommend fixing notes on network security
`* Tadiparthi - NACL was allow all from everywhere.`
`* Godwin - port 22 is allow to all so that need to be fix.`
`* Bhattarai - no negative`
`* Patel -  he allowed port 22 to all and nacl is allow to all traffic.`

### ⚠️ Vulnerability Vectors

Inquire about potential vulnerability vectors of their self-hosted software. They may have "patched" / addressed the vulnerability during their project implementation. If a suspected vulnerability is not on this list add a new bullet.  
Nested bullets should be in form: `* Last name - describe how software has this vulnerability and if it is currently vulnerable or has been patched`

* open site to everyopne `* Tadiparthi - his nacl is allow all to everyone even port 22.`, `* Godwin - port 22 is allow to all`, `* Bhattarai - port 9925 is open to everyone`, `* Patel - port 22 is open to all.` 
* Left default username / password
* Exposed admin interfaces
* Insecure configurations
* Users have destructive permissions to software assets
* Outdated versions of software or dependencies

---

### 💥 Live Troubleshooting / Future Fixes

Help someone with troubleshooting, get help with your troubleshooting, or find something you recommend they fix. Minimum of one is required.  
Nested bullets should be in form: `* Last name - description of situation`

* I received help from ____ with...
* I gave help to ____ by...
* According to ____ I need to fix... `* Godwin - fixed port 22 and only allow for your home and wrightstate ip.`, 
`* Bhattarai - he was using extra // on his url and recently added port 22 for wrightstate ip.` `* Patel - need to fix port 22 to only allow his home/wrighstate ip.`

* ____ needs to fix...

---
