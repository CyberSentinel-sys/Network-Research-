🛡️ Network Research Automation
📌 Overview
Network Research Automation is a fully automated reconnaissance and network scanning tool designed to run both locally and remotely via SSH. This project facilitates Whois lookups, Nmap scans, and anonymity verification while ensuring secure execution on a remote server.

The system comprises two components:

Local Script (combined.sh) – Executes pre-requisite checks, establishes a secure connection, and transfers tasks to the remote machine.
Remote Script (NR_remote.sh) – Performs network intelligence tasks on the target, including Whois and Nmap scanning.
🚀 Key Features
✔ Automated Dependency Verification – Installs and verifies essential tools such as nmap, whois, tor, sshpass, and jq.
✔ Anonymity Validation – Uses NIPE to check if the network traffic is routed through Tor.
✔ Secure Remote Execution – Automates SSH-based execution of network reconnaissance tasks.
✔ Comprehensive Scanning – Performs Whois lookups and Nmap scans for intelligence gathering.
✔ Automated Data Retrieval – Collects and saves scan results locally for post-analysis.

🛠️ Installation
1️⃣ Clone the Repository
bash
Copy code
git clone https://github.com/yourusername/network-research-automation.git
cd network-research-automation
2️⃣ Install Dependencies
Ensure your system has the required tools installed:

bash
Copy code
sudo apt update && sudo apt install -y sshpass curl cpanminus git nmap tor jq openssh-server



📖 Usage Guide:
The Network Research Automation tool operates in a structured manner, orchestrating local and remote execution to streamline network reconnaissance. Below is a detailed breakdown of the usage workflow.

1️⃣ Execute the Local Script
Run the main automation script:

bash
Copy code
bash combined.sh
The script will prompt for the following details:

Target domain or IP address (e.g., 8.8.8.8)
Remote server SSH username (e.g., kali)
Remote server IP address (e.g., 192.168.1.100)
SSH password (if not using SSH keys)
2️⃣ Local Script Execution Flow
Upon execution, the local script performs the following tasks:

Verifies anonymity by running NIPE to check Tor routing.
Ensures SSH is active on the remote machine and starts it if necessary.
Transfers the remote script (NR_remote.sh) securely to the target machine.
Executes remote scanning on the specified domain/IP.
3️⃣ Remote Script Execution Flow
Once deployed on the remote server, the remote script:

Fetches system information including:
Public IP address
Geographic location
Server uptime
Executes reconnaissance scans:
Whois Lookup: Gathers domain/IP registration details.
Nmap Scan: Identifies open ports and running services.
Stores results in /home/kali/Desktop/NR/ for retrieval.
4️⃣ Fetching Results
After execution, the local script automatically retrieves the scan results and stores them in:

bash
Copy code
~/Desktop/NR/
The output includes:

whois_res.txt – Whois lookup details.
nmap_res.txt – Nmap scan report.
🔧 System Requirements
Local Machine
OS: Linux (Ubuntu/Kali/Debian-based)
Required Tools: bash, sshpass, curl, cpanminus, git, nmap, tor, jq
Internet connection (for anonymity checks & Whois lookups)
Remote Server
OS: Linux-based
Required Tools: bash, openssh-server, nmap, whois
SSH access enabled
⚠️ Legal Disclaimer
This tool is designed for ethical security research and educational purposes only. Unauthorized network scanning or reconnaissance without proper authorization is illegal. Users must ensure compliance with applicable laws and obtain explicit permission before conducting any network assessments.
