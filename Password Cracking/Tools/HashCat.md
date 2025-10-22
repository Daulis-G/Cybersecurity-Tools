## HashCat🔐 The World's Fastest Password Recovery Tool!

HashCat is an advanced password recovery tool that supports a wide range of hashing algorithms. It is designed to crack password hashes using GPU acceleration, making it one of the fastest tools available for ethical hacking, penetration testing, and forensic analysis.

If you are on a Kali Linux machine, this tool usually comes pre-installed.

---

**⚠️ YOU WILL NEED WORDLISTS ⚠️**

---

## Use Cases

🔓 Recover lost passwords

🛡️ Audit password strength

🧑‍💻 Penetration testing

🕵️ Digital forensics

🔐 Cracking Wi-Fi handshakes (WPA/WPA2)

🧠 Educating about password security

---

## Installation

### On Kali Linux (Pre-installed)
```bash
# Verify installation
hashcat --version
```

### On Ubuntu/Debian
```bash
sudo apt update
sudo apt install hashcat
```

### On macOS
```bash
brew install hashcat
```

### From Source
```bash
git clone https://github.com/hashcat/hashcat.git
cd hashcat
make
sudo make install
```

---

## How To Use

### Basic Command Syntax
```bash
hashcat [options] <hash_file> <wordlist>
```

### Common Options

| Option | Description |
|--------|-------------|
| `-m` | Hash type (see hash modes below) |
| `-a` | Attack mode (0=Dictionary, 1=Combinator, 3=Brute-force, etc.) |
| `-o` | Output file for cracked passwords |
| `--show` | Show cracked passwords from potfile |
| `--force` | Ignore warnings (use with caution) |
| `-w` | Workload profile (1-4, higher = faster but more resource intensive) |
| `--status` | Enable automatic status updates |
| `--username` | Enable username parsing in hash file |

---

## Hash Modes (Common Examples)

| Hash Type | Mode (-m) |
|-----------|----------|
| MD5 | 0 |
| SHA1 | 100 |
| SHA256 | 1400 |
| NTLM | 1000 |
| WPA/WPA2 | 2500 |
| WPA-PMKID | 16800 |
| bcrypt | 3200 |

*To see all hash modes:*
```bash
hashcat --help | grep -i "hash modes"
```

---

## Example Usage

### 1. Cracking MD5 Hashes

**Step 1:** Create a file with your MD5 hash
```bash
echo "5f4dcc3b5aa765d61d8327deb882cf99" > hash.txt
```

**Step 2:** Run hashcat with a wordlist
```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

**Step 3:** View cracked passwords
```bash
hashcat -m 0 hash.txt --show
```

**Explanation:**
- `-m 0` specifies MD5 hash type
- `-a 0` specifies dictionary attack
- `hash.txt` is your file containing the hash
- `/usr/share/wordlists/rockyou.txt` is the wordlist to use

---

### 2. Cracking SHA256 Hashes

```bash
hashcat -m 1400 -a 0 sha256_hashes.txt /usr/share/wordlists/rockyou.txt
```

---

### 3. Cracking WPA/WPA2 Handshakes

**Step 1:** Capture the handshake (using airodump-ng)
```bash
airodump-ng --bssid [TARGET_MAC] -c [CHANNEL] -w capture wlan0mon
```

**Step 2:** Convert capture to hashcat format
```bash
hccapx2hashcat capture.hccapx > wpa_hash.txt
# OR use modern method with .cap file
cap2hashcat capture.cap wpa_hash.txt
```

**Step 3:** Crack with hashcat
```bash
hashcat -m 2500 -a 0 wpa_hash.txt /usr/share/wordlists/rockyou.txt
```

**For WPA-PMKID (newer method):**
```bash
hashcat -m 16800 -a 0 pmkid_hash.txt /usr/share/wordlists/rockyou.txt
```

---

### 4. Brute Force Attack

```bash
hashcat -m 0 -a 3 hash.txt ?a?a?a?a?a
```

**Character Sets:**
- `?l` = lowercase (a-z)
- `?u` = uppercase (A-Z)
- `?d` = digits (0-9)
- `?s` = special characters
- `?a` = all characters

**Example:** Crack 8-character password with lowercase + digits
```bash
hashcat -m 0 -a 3 hash.txt ?l?l?l?l?d?d?d?d
```

---

### 5. Using Rules for Enhanced Cracking

Rules modify wordlist entries to create variations:

```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

**Popular rule files:**
- `best64.rule` - Good balance of speed and coverage
- `dive.rule` - More extensive transformations
- `rockyou-30000.rule` - Very comprehensive

---

## Tips for Effective Use

### 🚀 Performance Optimization
1. **Use GPU acceleration** - HashCat automatically detects and uses GPU
2. **Adjust workload profile:**
   ```bash
   hashcat -m 0 -a 0 -w 3 hash.txt wordlist.txt
   ```
   - `-w 1` = Low (desktop usage)
   - `-w 2` = Default
   - `-w 3` = High (dedicated cracking)
   - `-w 4` = Nightmare (max performance)

3. **Use session management for long cracks:**
   ```bash
   hashcat -m 0 -a 0 --session my_session hash.txt wordlist.txt
   # Resume later with:
   hashcat --session my_session --restore
   ```

### 📋 Best Practices

1. **Start with common passwords**
   ```bash
   hashcat -m 0 hash.txt /usr/share/wordlists/fasttrack.txt
   ```

2. **Use multiple wordlists**
   ```bash
   cat wordlist1.txt wordlist2.txt > combined.txt
   hashcat -m 0 hash.txt combined.txt
   ```

3. **Check if already cracked**
   ```bash
   hashcat -m 0 hash.txt --show
   ```

4. **Monitor progress**
   - Press `s` during cracking for status
   - Press `p` to pause/resume
   - Press `q` to quit (saves session)

### 🎯 Wordlist Recommendations

- **rockyou.txt** - Most popular, 14 million passwords
  ```bash
  # Extract on Kali Linux:
  sudo gunzip /usr/share/wordlists/rockyou.txt.gz
  ```
- **SecLists** - Comprehensive collection
  ```bash
  git clone https://github.com/danielmiessler/SecLists.git
  ```
- **CrackStation** - Large wordlist (15GB)
- **Custom wordlists** - Create based on target context

### ⚠️ Troubleshooting

**Issue:** "No devices found"
- **Solution:** Update GPU drivers or use `--force` flag

**Issue:** Slow performance
- **Solution:** Increase workload with `-w 3` or `-w 4`

**Issue:** "Line-length exception"
- **Solution:** Hash format incorrect, verify hash type with `-m`

---

## Example Workflow for Beginners

```bash
# 1. Identify your hash type
echo "5f4dcc3b5aa765d61d8327deb882cf99" > target_hash.txt

# 2. Extract rockyou wordlist (if compressed)
sudo gunzip /usr/share/wordlists/rockyou.txt.gz

# 3. Start cracking (MD5 example)
hashcat -m 0 -a 0 target_hash.txt /usr/share/wordlists/rockyou.txt

# 4. Check results
hashcat -m 0 target_hash.txt --show

# 5. Try with rules if simple attack fails
hashcat -m 0 -a 0 target_hash.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

---

## Ethical Considerations

⚖️ **Always obtain proper authorization before testing!**

- Only crack passwords you have permission to test
- Use for legitimate security assessments
- Respect privacy and legal boundaries
- Document your findings professionally

---

## Additional Resources

- [Official HashCat Website](https://hashcat.net/hashcat/)
- [HashCat Wiki](https://hashcat.net/wiki/)
- [Hash Examples](https://hashcat.net/wiki/doku.php?id=example_hashes)
- [Hashcat Forums](https://hashcat.net/forum/)

---


