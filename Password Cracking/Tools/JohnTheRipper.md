# 🔓 John the Ripper - The OG Password Cracker

John the Ripper, the legendary password cracking tool that's been breaking passwords since 1996! Whether you're a penetration tester, security researcher, or simply curious about password security, John is your trusted sidekick for testing password strength and recovering lost credentials.

## 📋 Overview

John the Ripper is a fast, flexible, and feature-rich password cracking tool that supports hundreds of hash and cipher types. Originally developed for Unix systems, it now runs on 15+ different platforms including Windows, macOS, and Linux. It's completely free and open-source, making it one of the most popular password crackers in the cybersecurity community.

John uses multiple attack modes including dictionary attacks, brute-force, and its famous "incremental" mode which intelligently tries combinations based on character frequency analysis. It's designed to detect hash types automatically and comes with a built-in wordlist to get you started immediately.

## ✨ Features

-  **Multi-Platform Support** - Runs on Windows, Linux, macOS, and many Unix variants
-  **Auto-Detection** - Automatically detects hash types for hassle-free cracking
-  **Multiple Attack Modes** - Dictionary, brute-force, incremental, and hybrid attacks
-  **High Performance** - Optimized for speed with multi-core CPU support
-  **Customizable Rules** - Create custom mangling rules to modify wordlists
-  **Extensive Hash Support** - Cracks 500+ hash and cipher types
-  **Community Jumbo Patch** - Enhanced version with even more formats and features
-  **Session Management** - Save and resume cracking sessions
-  **Wordlist Mode** - Use custom dictionaries for targeted attacks
-  **External Modes** - Write your own cracking modes in C or scripting languages

## 💻 Installation

### Windows
```bash
# Download the Windows binary from the official website
# https://www.openwall.com/john/

# Extract the zip file
# Navigate to the run directory
cd john-*-jumbo-1-win64/run

# Run John
john.exe --test
```

### Linux (Debian/Ubuntu)
```bash
# Install from repository (basic version)
sudo apt update
sudo apt install john

# Or build from source for the Jumbo version (recommended)
sudo apt install git build-essential libssl-dev zlib1g-dev
git clone https://github.com/openwall/john.git
cd john/src
./configure && make -s clean && make -sj4

# Run John
../run/john --test
```

### macOS
```bash
# Install using Homebrew
brew install john-jumbo

# Or compile from source
git clone https://github.com/openwall/john.git
cd john/src
./configure && make -s clean && make -sj4

# Run John
john --test
```

## 🎮 How To Use

### Basic Hash Cracking
```bash
# Crack a password hash file
john hashfile.txt

# Crack with a specific wordlist
john --wordlist=/path/to/wordlist.txt hashfile.txt

# Show cracked passwords
john --show hashfile.txt
```

### Specifying Hash Format
```bash
# Crack MD5 hashes
john --format=raw-md5 hashes.txt

# Crack SHA-256 hashes
john --format=raw-sha256 hashes.txt

# List all supported formats
john --list=formats
```

### Using Rules
```bash
# Apply wordlist rules for mutations
john --wordlist=wordlist.txt --rules hashfile.txt

# Use specific rule set
john --wordlist=wordlist.txt --rules=Jumbo hashfile.txt
```

### Incremental Mode
```bash
# Use incremental brute-force (most powerful mode)
john --incremental hashfile.txt

# Use specific incremental mode
john --incremental=Digits hashfile.txt
```

### Session Management
```bash
# Name a session for later resumption
john --session=mysession hashfile.txt

# Resume a session
john --restore=mysession

# Check status of running session
john --status=mysession
```

### Cracking ZIP/RAR Files
```bash
# Extract hash from ZIP file
zip2john encrypted.zip > zip.hashes
john zip.hashes

# Extract hash from RAR file
rar2john encrypted.rar > rar.hashes
john rar.hashes
```

## 🔐 Supported Hash Types

John the Ripper supports a massive array of hash types. Here are some of the most common:

### Traditional Hashes
- MD5, MD4, MD2
- SHA-1, SHA-224, SHA-256, SHA-384, SHA-512
- NTLM, LM (Windows hashes)
- bcrypt, scrypt
- RIPEMD-128, RIPEMD-160

### System Hashes
- Unix crypt(3) and variants
- Windows NTLM/NTLMv2
- Kerberos tickets
- macOS keychain
- Linux shadow files

### Application Hashes
- WPA/WPA2 PSK
- PDF documents
- Microsoft Office files
- ZIP/RAR archives
- SSH private keys
- Bitcoin/cryptocurrency wallets
- 1Password, KeePass, LastPass

### Database Hashes
- MySQL, PostgreSQL
- MSSQL, Oracle
- MongoDB

### Web Application Hashes
- phpBB, Joomla, WordPress
- Django, Rails
- MediaWiki

*Note: The Jumbo community version supports 500+ additional formats!*

## 📚 Tutorials

### Tutorial 1: Cracking Linux Password Hashes

1. **Extract password hashes from /etc/shadow**
   ```bash
   sudo unshadow /etc/passwd /etc/shadow > mypasswords.txt
   ```

2. **Run John with default settings**
   ```bash
   john mypasswords.txt
   ```

3. **View cracked passwords**
   ```bash
   john --show mypasswords.txt
   ```

### Tutorial 2: Dictionary Attack with Rules

1. **Prepare your hash file** (one hash per line)
   ```
   user1:5f4dcc3b5aa765d61d8327deb882cf99
   user2:098f6bcd4621d373cade4e832627b4f6
   ```

2. **Download a wordlist** (like rockyou.txt)
   ```bash
   wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
   ```

3. **Run John with wordlist and rules**
   ```bash
   john --format=raw-md5 --wordlist=rockyou.txt --rules=Jumbo hashes.txt
   ```

4. **Monitor progress**
   ```bash
   john --status
   ```

### Tutorial 3: Cracking Windows NTLM Hashes

1. **Obtain NTLM hashes** (from password dump or SAM file)
   ```
   Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
   ```

2. **Save to file** (ntlm.txt)

3. **Crack with format specification**
   ```bash
   john --format=nt ntlm.txt
   ```

4. **Add wordlist for faster results**
   ```bash
   john --format=nt --wordlist=rockyou.txt ntlm.txt
   ```

## 💡 Tips & Tricks

### Performance Optimization
- **Use multiple cores**: John automatically uses all available CPU cores
- **Try single crack mode first**: `john --single hashfile.txt` - fast mode using username info
- **Optimize for your CPU**: Compile John from source for best performance on your hardware
- **Use GPU acceleration**: Check out the Jumbo version with OpenCL support for massive speed boosts

### Wordlist Strategies
- **Start with common passwords**: Use rockyou.txt or other breach compilations
- **Target-specific wordlists**: Create custom lists based on company names, locations, dates
- **Combine wordlists**: `cat list1.txt list2.txt | sort -u > combined.txt`
- **Use CeWL**: Generate wordlists from target websites for context-aware attacks

### Rules Magic
- **View available rules**: `john --list=rules`
- **Test rules first**: Use `--stdout` to see what your rules produce before running
- **Create custom rules**: Edit john.conf to add your own mangling rules
- **Stack rules**: Combine multiple rule sets for more variations

### Session Management
- **Always name your sessions**: Makes it easy to manage multiple cracking jobs
- **Check progress without interrupting**: `john --status=sessionname`
- **Pause gracefully**: Press Ctrl+C once (not twice!) to save state and exit
- **Resume automatically**: If John crashes, it can usually resume from checkpoint

### Format Detection
- **Let John auto-detect**: It's pretty good at identifying hash types
- **Verify format**: `john --list=formats | grep -i <hashtype>`
- **Test format**: Use `--format=<type>` with `--test` to verify support
- **Check hash examples**: Use `john --list=format-details` for hash examples

### Advanced Techniques
- **Mask attacks**: Use `--mask` for targeted brute-force with patterns (e.g., `?u?l?l?l?d?d`)
- **External modes**: Write custom Python/C code for specialized attack logic
- **Hybrid attacks**: Combine wordlist with mask or brute-force
- **Incremental tuning**: Edit john.conf to optimize incremental mode for specific scenarios
- **Benchmark formats**: `john --test --format=<type>` to see speed before committing

### Practical Tips
- **Hash identification**: Use `hash-identifier` or online tools if unsure of hash type
- **Pot file management**: John stores cracked passwords in `john.pot` - back it up!
- **Clean up sessions**: Remove old session files to avoid confusion
- **Combine with other tools**: Use John for hash cracking, Hashcat for GPU power
- **Stay legal**: Only crack passwords you have permission to test!
- **Keep updated**: The Jumbo community version gets frequent updates with new formats
- **Join the community**: Check out the john-users mailing list for tips and support

---

