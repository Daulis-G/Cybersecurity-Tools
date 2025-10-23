# 🔓 John the Ripper - The OG Password Cracker

John the Ripper, the legendary password cracking tool that's been breaking passwords since 1996! Whether you're a penetration tester, security researcher, or simply curious about password security, John is your trusted sidekick for testing password strength and recovering lost credentials.

## 📋 Overview

John the Ripper is a fast, flexible, and feature-rich password cracking tool that supports hundreds of hash and cipher types. Originally developed for Unix systems, it now runs on 15+ different platforms including Windows, macOS, and Linux. It's completely free and open-source, making it one of the most popular password crackers in the cybersecurity community.

John uses multiple attack modes including dictionary attacks, brute-force, and its famous "incremental" mode which intelligently tries combinations based on character frequency analysis. It's designed to detect hash types automatically and comes with a built-in wordlist to get you started immediately.

## ✨ Features

- **Multi-Platform Support** - Runs on Windows, Linux, macOS, and many Unix variants
- **Auto-Detection** - Automatically detects hash types for hassle-free cracking
- **Multiple Attack Modes** - Dictionary, brute-force, incremental, and hybrid attacks
- **High Performance** - Optimized for speed with multi-core CPU support
- **Customizable Rules** - Create custom mangling rules to modify wordlists
- **Extensive Hash Support** - Cracks 500+ hash and cipher types
- **Community Jumbo Patch** - Enhanced version with even more formats and features
- **Session Management** - Save and resume cracking sessions
- **Wordlist Mode** - Use custom dictionaries for targeted attacks
- **External Modes** - Write your own cracking modes in C or scripting languages

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
git clone https://github.com/openwall/john -b bleeding-jumbo john
cd john/src
./configure && make -s clean && make -sj4
cd ../run
./john --test
```

### macOS
```bash
# Using Homebrew
brew install john-jumbo

# Or build from source
git clone https://github.com/openwall/john -b bleeding-jumbo john
cd john/src
./configure && make -s clean && make -sj4
cd ../run
./john --test
```

## 🚀 Usage

### Basic Commands

```bash
# Crack a password file with auto-detection
john hashfile.txt

# Use a specific wordlist
john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt

# Use a wordlist with rules
john --wordlist=passwords.txt --rules hashfile.txt

# Brute-force attack
john --incremental hashfile.txt

# Show cracked passwords
john --show hashfile.txt

# Resume a previous session
john --restore

# Check cracking status
john --status
```

### Advanced Options

```bash
# Specify hash format
john --format=raw-md5 hashfile.txt

# Use specific session name
john --session=mysession hashfile.txt

# Limit character set for brute-force
john --incremental=digits hashfile.txt

# Use GPU acceleration (requires OpenCL)
john --format=raw-md5-opencl hashfile.txt

# Generate wordlist mutations without cracking
john --wordlist=words.txt --rules --stdout > mutations.txt

# Crack with mask attack (e.g., Password + 2 digits)
john --mask='Password?d?d' hashfile.txt
```

### Hash Format Examples

```bash
# List all supported formats
john --list=formats

# List subformats
john --list=subformats

# Test a specific format
john --test --format=raw-sha256

# Common format names:
# raw-md5, raw-sha1, raw-sha256, nt (NTLM)
# bcrypt, descrypt, md5crypt, sha256crypt, sha512crypt
```

## 📚 Tutorials

### 🎥 Video Tutorials

Ready to see John the Ripper in action? These video tutorials will guide you through everything from basic usage to advanced techniques:

1. **"John the Ripper - Complete Beginner's Guide"**
   - Perfect starting point for newcomers! Covers installation, basic commands, and your first successful password crack. Learn the fundamentals of dictionary attacks and how to interpret John's output.

2. **"Advanced Password Cracking with John the Ripper"**
   - Take your skills to the next level! Explores rule-based attacks, custom wordlist creation, hash format identification, and session management for long-running jobs.

3. **"John the Ripper: Mask Attacks & GPU Acceleration"**
   - Supercharge your cracking! Demonstrates how to use mask attacks for pattern-based passwords and leverage GPU power with OpenCL for massive speed improvements.

### 📖 Official Resources

Want to dive deeper? Check out these trusted resources straight from the source:

- **[Openwall Documentation](https://www.openwall.com/john/doc/)** - The official documentation hub with comprehensive guides, tutorials, and technical references for all John the Ripper features.

- **[John the Ripper Official Website](https://www.openwall.com/john/)** - Download the latest versions, check release notes, and explore community-contributed patches and enhancements.

- **[Openwall Community Wiki](https://openwall.info/wiki/john)** - Community-maintained knowledge base with real-world examples, troubleshooting tips, and advanced configuration guides.

---

## 💡 Pro Tips and Best Practices

### Performance Optimization

- **Use the Jumbo version**: It includes optimizations and support for many more hash types
- **Choose the right attack mode**: Dictionary attacks are faster than brute-force for common passwords
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

## 🔒 Legal and Ethical Considerations

**⚠️ Important Warning**: Password cracking tools like John the Ripper are powerful and must be used responsibly.

### Legal Use Cases:
- Penetration testing with explicit written authorization
- Security audits for your own systems
- Recovering lost passwords on your own accounts
- Educational purposes in controlled environments
- Security research with proper ethical approval

### Illegal Activities (Never Do This!):
- Cracking passwords without authorization
- Accessing systems you don't own or have permission to test
- Using cracked passwords for unauthorized access
- Distributing cracked passwords

**Remember**: Unauthorized access to computer systems is illegal in most countries and can result in serious criminal charges. Always obtain written permission before testing any system you don't own.

---

## 🤝 Contributing

John the Ripper is open-source! Want to contribute?
- Report bugs on the mailing list
- Submit patches for new hash formats
- Improve documentation
- Share optimizations and rules

Visit the [Openwall community](https://www.openwall.com/lists/john-users/) to get involved!

---

## 📜 License

John the Ripper is released under the GNU General Public License (GPL) v2. The community-enhanced "Jumbo" version includes additional code under compatible licenses.

---

*Happy (ethical) cracking! 🔓*
