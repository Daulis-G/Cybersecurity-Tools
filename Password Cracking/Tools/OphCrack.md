# OphCrack 🔓

## Overview 🔍

OphCrack is a Windows password cracker based on rainbow tables. It's one of the most efficient implementations of the rainbow table technique for password recovery.

## Key Features ✨

- **Free and Open Source**: Available at no cost
- **Cross-Platform**: Works on Windows, Linux, and macOS
- **LiveCD Available**: Boot from USB/CD without installation
- **GUI and CLI**: User-friendly interface plus command-line options
- **Rainbow Tables**: Uses pre-computed hash chains
- **Real-time Graphs**: Visual representation of cracking progress

## Installation 💾

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

## Usage Examples 🎯

### Basic GUI Usage
1. Launch OphCrack
2. Click "Load" → "PWDUMP file" or "Local SAM"
3. Click "Tables" → Select rainbow table directory
4. Click "Crack" to start the process

### Command Line
```bash
# Crack from pwdump file
ophcrack -g -d /path/to/tables/ -t XP -f hashes.txt

# Crack local SAM (requires root/admin)
sudo ophcrack -g -d /path/to/tables/ -t Vista

# Specify output file
ophcrack -g -d /tables/ -t XP -f hashes.txt -o results.txt
```

### LiveCD Usage
1. Download OphCrack LiveCD ISO
2. Burn to USB or CD
3. Boot from media
4. OphCrack automatically starts and detects Windows partitions
5. Select partition and begin cracking

## Rainbow Tables 🌈

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

## CTF & Competition Tips 💡

### Quick Wins
1. **LiveCD Method**
   - Fastest method for offline attacks
   - No installation needed
   - Automatically detects Windows installations

2. **Start with Free Tables**
   - XP Free tables work well for simple passwords
   - Vista Free tables cover basic Windows Vista/7 passwords
   - Good for quick wins in CTF scenarios

3. **LM Hash Priority**
   - LM hashes (older Windows) crack MUCH faster
   - Always check if LM hashes are available
   - Can crack in minutes vs hours for NTLM

### Competition Strategy

1. **Hybrid Approach**
   - Use OphCrack for initial quick cracks
   - Switch to Hashcat for the remaining hashes
   - OphCrack excels at simple passwords

2. **Table Selection**
   - Match tables to hash type (LM vs NTLM)
   - Larger tables = better coverage but slower
   - Prioritize speed in time-limited scenarios

3. **Multiple Targets**
   - Load all hashes at once
   - OphCrack processes multiple hashes simultaneously
   - Efficient for multiple user accounts

### Time-Saving Techniques

1. **Pre-stage Rainbow Tables**
   - Download and configure tables before competition
   - Keep tables on fast storage (SSD)
   - Organize by hash type for quick access

2. **Know the Limitations**
   - Free tables limited to ~99.9% of alphanumeric passwords ≤14 chars
   - Complex passwords may not be in tables
   - Modern Windows (8+) more resistant

3. **Combine with Other Tools**
   ```bash
   # Dump hashes first
   fgdump.exe
   
   # Try OphCrack first (fast)
   ophcrack -f hashes.txt
   
   # If unsuccessful, use Hashcat for remaining
   hashcat -m 1000 remaining.txt wordlist.txt
   ```

### Common Pitfalls to Avoid

- **Insufficient RAM**: Ensure enough memory for table loading
- **Wrong Table Type**: LM tables won't work on NTLM hashes
- **Missing Dependencies**: Ensure all libraries installed
- **Permissions**: Need admin/root to access SAM file
- **Table Path Issues**: Verify correct path to rainbow tables
