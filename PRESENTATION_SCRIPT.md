# PRESENTATION SCRIPT — Network Research Automation
### Copy-paste into Canva / PowerPoint to build slides

---

## SLIDE 1 — Title Slide

**Headline:** Network Research Automation
**Subtitle:** Tor-Anonymized Reconnaissance via SSH Orchestration
**Footer:** CyberSentinel-sys | Ethical Security Research

---

## SLIDE 2 — The Problem

**Headline:** Manual Recon Is Slow, Loud & Traceable

**Bullet points:**
- Traditional scanning exposes the operator's real IP
- Manual SSH + tool execution is error-prone and slow
- No standardized output makes post-analysis difficult
- Switching between local/remote contexts breaks workflow

**Visual suggestion:** Red "exposed" icon vs green "anonymized" icon

---

## SLIDE 3 — The Solution

**Headline:** Automated, Anonymous, Orchestrated

**Bullet points:**
- Two-script framework: local orchestrator + remote executor
- Enforces Tor anonymity (via NIPE) *before* any packet leaves
- Automates SSH deployment, scan execution, and result retrieval
- Structured output: `whois_res.txt` + `nmap_res.txt`

**Visual suggestion:** Arrow from local → Tor cloud → remote server → results

---

## SLIDE 4 — How It Works (Architecture)

**Headline:** Execution Flow

**Steps (numbered list):**
1. Operator runs `combined.sh` on local Kali machine
2. NIPE verifies Tor is active — aborts if not
3. Script SSH's into remote server, transfers `NR_remote.sh`
4. Remote script executes: fetches geo/IP info, runs Whois + Nmap
5. Results written to remote `/Desktop/NR/`
6. Local script SCP-pulls results back to operator machine

**Visual suggestion:** Use the Mermaid flowchart from README as the graphic

---

## SLIDE 5 — Tech Stack

**Headline:** Built With

| Component | Tool |
|---|---|
| Scripting | Bash |
| Anonymity | Tor + NIPE |
| Remote Exec | SSH / sshpass |
| Recon | nmap, whois |
| Data | jq, curl |
| OS | Kali Linux |

---

## SLIDE 6 — Key Results / Demo

**Headline:** What It Produces

**Sample output labels:**
- `whois_res.txt` → Registrar, creation date, name servers, registrant
- `nmap_res.txt` → Open ports (22, 80, 443...), service versions, OS guess

**Visual suggestion:** Dark terminal screenshot showing nmap output

---

## SLIDE 7 — Security & Ethics

**Headline:** Built Responsible

**Bullet points:**
- Operator identity protected at all times via Tor enforcement
- No hardcoded credentials — environment variable driven
- Designed for authorized engagements only
- Compliant with CFAA, Computer Misuse Act, and GDPR principles

---

## SLIDE 8 — Takeaways / CTA

**Headline:** What This Demonstrates

**Bullet points:**
- Deep understanding of Linux networking and SSH automation
- Practical OPSEC / anonymity implementation
- Red team recon workflow design
- Bash scripting for security automation

**Footer CTA:** github.com/CyberSentinel-sys | Open to Red Team / Security Engineering roles
