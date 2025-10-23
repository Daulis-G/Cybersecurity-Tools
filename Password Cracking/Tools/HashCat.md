## 
 HashCat🔐 The World's Fastest Password Recovery Tool!
HashCat is an advanced password recovery tool that supports a wide range of hashing algorithms. It is designed to crack password hashes using GPU acceleration, making it one of the fastest tools available for ethical hacking, penetration testing, and forensic analysis.
If you are on a Kali Linux machine, this tool usually comes pre-installed.
---
**
⚠️ YOU WILL NEED WORDLISTS ⚠️
**
---
## 
 Use Cases
🔓 Recover lost passwords
🛡️ Audit password strength
🧑‍💻 Penetration testing
🕵️ Digital forensics
🔐 Cracking Wi-Fi handshakes (WPA/WPA2)
🧠 Educating about password security
---
## 
 Installation
### 
 On Kali Linux (Pre-installed)
```
bash
# Verify installation
hashcat --version
```
### 
 On Ubuntu/Debian
```
bash
sudo apt update
sudo apt install hashcat
```
### 
 On macOS
```
bash
brew install hashcat
```
---
## 
 How To Use
### 
 Basic Command Syntax
```
bash
hashcat [options] <hashfile> <wordlist>
```
### 
 Common Options
| Option | Description |
|--------|-------------|
| `-m`   | Hash type (see hash modes below) |
| `-a`   | Attack mode (0=Dictionary, 1=Combinator, 3=Brute-force, etc.) |
| `-o`   | Output file for cracked passwords |
| `--show` | Show cracked passwords from potfile |
| `--force` | Ignore warnings (use with caution) |
| `-w`   | Workload profile (1-4, higher = faster but more resource intensive) |
| `--status` | Enable automatic status updates |

---
## Usage Examples and Common Commands
- Crack MD5 hashes with a wordlist
```
bash
hashcat -m 0 -a 0 hashes.txt /path/to/wordlist.txt
```
- Bruteforce lowercase 6 characters on NTLM
```
bash
hashcat -m 1000 -a 3 hashes.txt ?l?l?l?l?l?l
```
- Use rules with a wordlist
```
bash
hashcat -m 1800 -a 0 hashes.txt rockyou.txt -r rules/best64.rule
```
- Restore a previous session
```
bash
hashcat --restore --session myjob
```

### Viewing All Options
To see the full list of command-line options and descriptions, run:
```
bash
hashcat --help
```
Useful flags you will find in the help output (quick reference):
- Hash mode: `-m <id>` — selects the hash algorithm (e.g., 0=MD5, 100=SHA1, 22000=WPA-PBKDF2/PMKID).
- Attack mode: `-a <mode>` — defines the attack type (0=dict, 1=combo, 3=mask, 6/7=hybrids).
- Output file: `-o <file>` — write cracked credentials to a file.
- Session management: `--session <name>`, `--restore` — name and resume sessions.
- Rule files: `-r <rulefile>` — apply mangling rules to wordlist candidates.
- Workload profile: `-w 1..4` — tune performance vs. responsiveness.
- Device selection: `-d <devices>` or `-D <type>` — pick specific GPUs/CPUs (e.g., `-D 1` for CPU, `-D 2` for GPU) and `-d 1,2` to target device indices.
- Status display: `--status`, `--status-timer <sec>` — periodic progress updates in the console.
- Potfile control: `--potfile-disable`, `--potfile-path <path>` — manage where cracked hashes are stored.
- Restore point/output: `--restore-disable`, `--logfile-disable` — control state/log writing.
- Performance tuning: `--kernel-accel`, `--kernel-loops`, `--gpu-temp-abort`, `--hwmon-temp-abort`.
- Limits: `--skip <N>`, `--limit <N>` — process only part of the keyspace.
- Masks and charsets: `-1`, `-2`, `-3`, `-4` — define custom charsets for mask attacks.

Shortlist of what key options control:
- Hash mode: which hashing algorithm your input represents.
- Attack mode: how candidates are generated and tested.
- Output file: where successful cracks are saved.
- Session: naming and resuming long-running jobs safely.
- Rules: augment wordlists with transformations.
- Workload: CPU/GPU utilization profile.
- Device: choose which hardware runs the job.
- Status: frequency and format of progress information.

Tip: Combine `--help` with `grep` to find specific topics quickly, e.g. `hashcat --help | grep -i device`.
