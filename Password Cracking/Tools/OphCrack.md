# 🔓 OphCrack
OphCrack is a Windows password cracker based on rainbow tables. It's one of the most efficient implementations of the rainbow table technique for password recovery.
## ✨ Key Features
- **Free and Open Source**: Available at no cost
- **Cross-Platform**: Works on Windows, Linux, and macOS
- **Rainbow Tables**: Uses pre-computed hash chains
- **Real-time Graphs**: Visual representation of cracking progress
  
## 💾 Installation
### Windows
```bash
# Download from official site
wget https://ophcrack.sourceforge.io/download.php
# Or use package manager
choco install ophcrack
```
### Linux
```bash
# Debian/Ubuntu
sudo apt-get install ophcrack
# Arch
sudo pacman -S ophcrack
# From source
git clone https://gitlab.com/objectifsecurite/ophcrack.git
cd ophcrack
./configure
make
sudo make install
```
### macOS
```bash
brew install ophcrack
```
## 🎯 **How To Use**
### Basic GUI Usage
1. Launch OphCrack
2. Click "Load" → "PWDUMP file" or "Local SAM"
3. Click "Tables" → Select rainbow table directory
4. Click "Crack" to start the process
## 🌈 Rainbow Tables
### Free Tables
- **XP Free Fast**: ~700MB, alphanumeric passwords ≤14 chars
- **XP Free Small**: ~380MB, subset of Fast tables
- **Vista Free**: ~450MB, basic Vista/7/8 passwords
### Paid Tables
- **XP Special**: ~8GB, extended character set
- **Vista Special**: ~8GB, comprehensive Vista+ coverage
- **Better coverage and success rates**
### Downloading Tables
```bash
# Create directory structure
mkdir -p ~/ophcrack/tables
# Download free tables
wget https://ophcrack.sourceforge.io/tables.php
# Extract
unzip tables_vista_free.zip -d ~/ophcrack/tables/
```

## 📚 Tutorials
### Recommended Guides and Videos
- **[OphCrack Official Tutorial](https://ophcrack.sourceforge.io/)**: Comprehensive step-by-step guide from the official documentation covering installation, rainbow table setup, and basic usage
- **[HackerSploit OphCrack Tutorial (YouTube)](https://www.youtube.com/results?search_query=ophcrack+tutorial)**: Video walkthrough demonstrating Windows password recovery from start to finish, including SAM file extraction
- **[How to Crack Windows Passwords with OphCrack Live CD](https://null-byte.wonderhowto.com/)**: Detailed guide on using OphCrack's bootable live CD to recover passwords without OS access
- **[Password Cracking with Rainbow Tables - Theory and Practice](https://www.offensive-security.com/)**: In-depth tutorial explaining rainbow table theory and practical OphCrack applications

## 💡 Tips & Tricks
### Best Practices and Time-Saving Techniques
1. **Start with Free Tables First** - Test with the free XP/Vista tables before investing in paid versions to gauge success probability
2. **Use OphCrack Live CD for Maximum Success** - Booting from the live CD bypasses OS security and provides direct SAM access
3. **Combine Multiple Rainbow Tables** - Load several table sets simultaneously to increase coverage and crack rates
4. **Sort by Password Length** - Focus on shorter passwords first as they crack significantly faster (statistics show 70%+ of passwords are ≤8 chars)
5. **Keep Tables on Fast Storage** - Store rainbow tables on SSDs rather than HDDs to dramatically reduce lookup times
6. **Check for Empty/Blank Passwords First** - OphCrack can instantly identify accounts with no password - always check these before running full tables
7. **Use the Right Table for the OS Version** - Vista/7/8/10 require NTLM tables while XP works better with LM tables
8. **Monitor the Success Rate Graph** - If progress stalls after 15-20 minutes, the password likely isn't in your current tables
9. **Export Results Regularly** - Save cracked passwords periodically in case of crashes or interruptions
10. **Combine with Other Tools** - Use OphCrack for simple passwords, then switch to hashcat or John the Ripper for complex ones
