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
