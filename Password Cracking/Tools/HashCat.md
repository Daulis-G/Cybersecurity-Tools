# HashCat

HashCat is the world's fastest password recovery tool that supports a wide range of hashing algorithms. It uses GPU acceleration to crack password hashes, making it essential for ethical hacking, penetration testing, and forensic analysis.

## Requirements

- GPU with CUDA or OpenCL support (for optimal performance)
- Wordlists for dictionary attacks
- Hash file containing password hashes to crack
- Basic understanding of hash types and attack modes
- Sufficient disk space for wordlists and potfiles

## Setup

1. On Kali Linux, HashCat is pre-installed. Verify installation with `hashcat --version`
2. On Ubuntu/Debian, install via `sudo apt update && sudo apt install hashcat`
3. On macOS, install via Homebrew: `brew install hashcat`
4. Alternatively, compile from source: `git clone https://github.com/hashcat/hashcat.git && cd hashcat && make && sudo make install`
5. Download wordlists (rockyou.txt is commonly used) to `/usr/share/wordlists/`
6. Test installation by running `hashcat --benchmark` to check GPU support

## Usage Examples and Common Commands

**Basic dictionary attack:**
```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

**Crack MD5 hashes with output file:**
```bash
hashcat -m 0 hash.txt wordlist.txt -o cracked.txt
```

**Brute-force attack (mask attack):**
```bash
hashcat -m 0 -a 3 hash.txt ?a?a?a?a?a?a
```

**Show already cracked passwords:**
```bash
hashcat -m 0 hash.txt --show
```

**Crack WPA/WPA2 handshake:**
```bash
hashcat -m 22000 capture.hc22000 wordlist.txt
```

**Common hash modes:**
- `-m 0` = MD5
- `-m 100` = SHA1
- `-m 1000` = NTLM
- `-m 1400` = SHA256
- `-m 3200` = bcrypt
- `-m 22000` = WPA/WPA2

**Attack modes:**
- `-a 0` = Dictionary attack
- `-a 1` = Combinator attack
- `-a 3` = Brute-force/Mask attack
- `-a 6` = Hybrid wordlist + mask
- `-a 7` = Hybrid mask + wordlist

### Links to Official Documentation and Tutorials

- Official HashCat website: https://hashcat.net/hashcat/
- GitHub repository: https://github.com/hashcat/hashcat
- HashCat Wiki: https://hashcat.net/wiki/
- Hash mode reference: https://hashcat.net/wiki/doku.php?id=example_hashes
- Mask attack guide: https://hashcat.net/wiki/doku.php?id=mask_attack

### Tips & Tricks for Competition Scenarios

1. Always identify the hash type first using tools like `hashid` or `hash-identifier` before running HashCat
2. Start with common wordlists like rockyou.txt, then move to more specialized lists if needed
3. Use `--force` flag if you encounter warnings, but be aware it may cause instability
4. Monitor progress with status output - press 's' during execution to see current status
5. Utilize the potfile (`~/.hashcat/hashcat.potfile`) - it stores all previously cracked hashes automatically
6. For competitions, try combination attacks (-a 1) with small wordlists to quickly find password patterns
7. Use incremental mask attacks starting with shorter lengths (?a?a?a?a) before longer ones to find weak passwords faster
8. Leverage rule-based attacks with popular rule sets like `best64.rule` or `dive.rule` to modify wordlist entries
9. Check for already cracked hashes first with `--show` to save time on duplicate work
10. If GPU isn't available, HashCat can still run on CPU with `--force` but will be significantly slower
