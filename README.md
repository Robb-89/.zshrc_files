# Zsh Operator Configs (HTB + Bug Bounty + Productivity)

This repo contains multiple `.zshrc` configurations I’ve built for my own systems over time.  
They are tuned for **pentesting labs, CTF challenges, bug bounty research, and daily development work**.  

⚠️ **Important Notes**  
- These files are **customized for my personal machines** (paths, tools, VPN profiles, wordlists). If you want to use them, you’ll likely need to adapt paths, package names, and environment variables.  
- All included aliases/functions are intended for **legal and authorized use only**. Do not use these against systems you do not own or lack explicit permission to test.  
- Many helpers reference tools like `nmap`, `ffuf`, `gobuster`, `nuclei`, etc. — you’ll need to install them separately.  

---

## Core Features

### Productivity / Quality of Life
- **History optimization** — prevents duplicates, shares history across shells, increases size.  
- **Aliases** — `ll`, `la`, `cls`, `please` (re-run last command with sudo), quick `cd` (`..`, `...`, `....`).  
- **Git shortcuts** — `gs`, `ga`, `gc`, `gp`, `gco`, `gcb`, `glog`.  
- **Docker helpers** — `dps`, `dpsa`, `di`, `dexec`, `dclean`, `dlog`.  
- **Quick servers** — `serve`, `serve80`, `serve443`, `servephp`, `ftp-server`.  

### Networking & System Info
- `sysinfo` (neofetch), `diskspace`, `meminfo`, `cpuinfo`.  
- `myip`, `publicip`, `localips`, `gateway`.  
- `ports` / `openports` (netstat, nmap).  
- VPN helpers (`htb-up`, `htb-down`) for HackTheBox/OpenVPN configs.  

### Recon / Enumeration
- **Nmap** profiles:  
  - `nmapscan` (aggressive scan)  
  - `fullnmap` (all ports)  
  - `stealthnmap` (syn stealth)  
  - `udpscan`, `vulnscan`  
  - `bb-nmap` (scaffolded quick/full scans with workspace output)  
- **Web scanning**:  
  - `webscan` (gobuster dirs)  
  - `subscan` (gobuster DNS)  
  - `dirhunt` (ffuf/gobuster wrapper with wordlist autodetect)  
  - `bb-web` (tech detection, directory brute, nuclei scan for a target URL)  
- **Subdomain discovery**:  
  - `sublist3r`, `amass-enum`, `subenum` (passive-first, multi-tool combo).  
- **URL collection**:  
  - `gather_urls` (gau + waybackurls).  
- **Probing**:  
  - `probe` (httpx, detect live hosts + tech stack).  

### Exploitation Helpers
- **Reverse shell payloads** (`reverse-shell` or `reverse-shell-payload`) — print common payloads for Bash, Python, PHP, Netcat. (⚠️ These only print payloads; you must use responsibly and with authorization.)  
- **Metasploit** — `msfconsole`.  
- **Searchsploit** — `searchsploit`.  
- **Hash cracking** — `hashcat-md5`, `hashcat-sha1`, `john`.  
- **Password attacks** — `hydra-ssh`, `hydra-ftp`.  

### Web App / Bug Bounty Toolkit
- **BurpSuite** — `burp`  
- **OWASP ZAP** — `zaproxy`  
- **sqlmap** — `sqlmap`  
- **wpscan** — `wpscan`  
- **ffuf** — `ffuf` (fuzzing URLs)  
- **nuclei** — `scan_nuclei` (rate-limited, safe defaults)  
- **param mining** — `param_miner` (Arjun wrapper for discovering parameters).  

### Orchestration (Automated Workflows)
- **Workspace scaffolding** — `mkbb target.com`  
  Creates a structured folder tree (`recon/`, `web/`, `loot/`, `notes/`, etc.) with timestamps.  
- **bb-recon** — passive-first recon pipeline (subenum → probe → gather_urls).  
- **bb-web** — targeted web enum with gobuster + whatweb + nuclei.  
- **bb-nmap** — scaffolded nmap quick or full scan with workspace output.  

---

## Ethical Usage

These `.zshrc` configs are **not “hacking tools” by themselves**, but they make it easier to orchestrate and automate common security testing workflows.  
You must:  
1. Only use them against **systems you own, control, or have explicit permission to test** (e.g., HackTheBox, CTF labs, or bug bounty targets within scope).  
2. Understand what each alias/function does before running it — e.g., `fullnmap` can be aggressive.  
3. Take responsibility for your actions. I provide these for educational purposes and **my own use**.  

---

## Machine-Specific Setup

- These configs assume certain directories exist (`~/hacking`, `~/tools`, `~/wordlists`).  
- Wordlists (`seclists`, `dirbuster`, etc.) may need path adjustments.  
- My HackTheBox OpenVPN profile is referenced through an environment variable (`HTB_OVPN`) that should be set in `~/.zshrc.local`.  
- Certain banners, ASCII art, and folder trees are purely cosmetic or tuned for my environment.  

If you clone this repo, expect to:  
- Edit paths in `PATH` setup.  
- Update aliases to match where your tools are installed.  
- Configure `~/.zshrc.local` for private settings (see the example file).  

---

## Getting Started

1. Clone the repo and symlink `.zshrc` (see instructions above).  
2. Copy `.zshrc.local.example` to `~/.zshrc.local` and customize it.  
3. Install missing tools (`nmap`, `ffuf`, `httpx`, `amass`, `docker`, etc.).  
4. Start small: run `mkbb example.com`, then try `bb-recon example.com`.  

---

## Contributing / Sharing

I built these files for **my own computers**, but feel free to fork and adapt.  
If you share publicly, keep in mind:  
- Strip secrets and private configs.  
- Add your own disclaimer.  
- Adapt tool paths to your environment.  

---

## License

MIT (do what you want, just keep attribution).  
But more importantly: **Use responsibly.**
