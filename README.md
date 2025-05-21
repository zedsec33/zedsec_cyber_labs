# 🧨 ZedSec Cyber Lab Architectures

Welcome to the **ZedSec BlackCell Cyber Lab Repository** – a modular, powerful, and surgical set of lab setups tailored for offensive security, malware analysis, and real-world adversarial simulation.

---

## 🧠 Lab 1: Offensive Operations Lab

### 🔧 Purpose
- Red Teaming
- Reverse Shell Payloads
- C2 Infrastructure

### 🖥️ Host Setup
```bash
sudo pacman -S virtualbox python python-pip wireshark nmap net-tools
```

### 📦 VMs
| VM       | OS         | Role      |
|----------|------------|-----------|
| Kali     | Kali Linux | Attacker  |
| Win10    | Win10 x86  | Victim    |

### 📡 Network
- VirtualBox Host-Only Adapter

### 🛠 Automation (bash)
```bash
#!/bin/bash
vboxmanage createvm --name Attacker --register
vboxmanage createvm --name Victim --register
# Add more VBox automation like attaching ISOs, CPUs, memory, networking...
```

---

## 🔬 Lab 2: Malware Dev & RE Lab

### 🔧 Purpose
- Build/Analyze malware safely
- Static & Dynamic RE

### 🧰 Tools
- VirtualBox
- FLARE VM
- REMnux
- Wireshark, Fakenet-NG
- x64dbg, Ghidra, PEStudio

### 🛠 Automation (Vagrant + Shell)
```bash
# Vagrantfile sample for Win10 + FLARE
Vagrant.configure("2") do |config|
  config.vm.box = "gusztavvargadr/windows-10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end
end
```

---

## 🌐 Lab 3: Web Pentesting & SQLi Lab

### 🔧 Purpose
- SQL Injection
- XSS/LFI
- Web App Recon

### 🧰 Apps
- DVWA, Mutillidae, WordPress (old plugins)

### 🛠 Automation
```bash
sudo apt update && sudo apt install apache2 php mysql-server php-mysql
wget https://github.com/digininja/DVWA/archive/master.zip
unzip master.zip && mv DVWA* /var/www/html/dvwa
```

---

## 🎭 Lab 4: Network Attacks Lab

### 🔧 Purpose
- ARP Spoofing
- Packet Sniffing
- MITM

### 🧰 Tools
- Scapy
- Bettercap
- Wireshark

### 🛠 Automation
```bash
sudo pacman -S scapy wireshark-qt bettercap
```

---

## 🧪 Lab 5: Social Engineering & Phishing Lab

### 🔧 Purpose
- Email Spoofing
- Payload Drop
- Rubber Ducky Testing

### 🛠 Automation
```bash
# Install SET
git clone https://github.com/trustedsec/social-engineer-toolkit.git
cd social-engineer-toolkit && pip install -r requirements.txt
python setup.py install
```

---

## 💣 Lab 6: Exploit Dev & Fuzzing Lab

### 🔧 Purpose
- Buffer Overflows
- SEH Chains

### 🧰 Tools
- Immunity Debugger + Mona.py
- SLMail, Vulnserver

### 🛠 Automation
```powershell
# Windows setup
choco install immunitydebugger
# Copy mona.py into %ProgramFiles%\Immunity Debugger\PyCommands
```

---

## 📡 Lab 7: Multi-Agent C2 Lab

### 🔧 Purpose
- GitHub C2
- Multi-repo command polling

### 📦 GitHubC2 Skeleton
```python
import requests, base64
repo = 'https://api.github.com/repos/youruser/yourrepo/contents/task.txt'
token = 'ghp_XXXX'
r = requests.get(repo, headers={'Authorization': f'token {token}'})
cmd = base64.b64decode(r.json()['content']).decode()
```

### 🛠 Automation
```bash
echo "echo Y21kIC9jICdzZWN1cml0eSB0ZXN0aW5nJyA+IHJlc3VsdC50eHQ=" | base64 -d > task.sh
```

---

## 📦 Wordlists, Payloads & Resources
- `PayloadsAllTheThings`
- `awesome-wordlists`
- `Wordlist-Hub`

Clone them into `tools/` for seamless integration into fuzzers & brute-force scripts.

```bash
git clone https://github.com/swisskyrepo/PayloadsAllTheThings tools/payloads
```

---

## 🔥 Strategy Profiles

| Profile        | Labs Used                                  |
|----------------|---------------------------------------------|
| **Strike Lab** | 1, 3, 4, 5                                  |
| **Analysis Lab** | 2, 6, 7                                    |
| **Legacy Lab** | 6 (Win7)                                    |
| **OPSEC Lab**  | 1, 2, 7 with focus on stealth & evasion     |

---

## 🧠 ZedSec Lab Execution Tips

- Use snapshots aggressively
- Set networking to Host-Only or Internal NAT
- Never leak lab traffic to public networks
- Combine automation (Vagrant + shell scripts + VBoxManage)

---

> ⚔️ Build labs that strike fast, hide deep, and train hard.

Licensed for ethical use only.

**– ZedSec BlackCell**

