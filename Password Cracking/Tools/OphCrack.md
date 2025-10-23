# OphCrack

OphCrack is a free Windows password cracker based on rainbow tables. It is a very efficient implementation of rainbow tables done by the inventors of the method. It comes with a Graphical User Interface and runs on multiple platforms.

## Requirements

- **Operating System**: Windows, Linux, or macOS
- **Rainbow Tables**: Pre-computed tables for password cracking (can be downloaded separately)
- **Target**: Windows password hashes (LM and NTLM)
- **RAM**: Sufficient memory to load rainbow tables (varies by table size)
- **Bootable Version**: Available as LiveCD for offline password recovery

## Setup

1. **Download OphCrack**
   ```bash
   # For Linux/Kali
   sudo apt-get install ophcrack
   
   # Or download from official website
   # https://ophcrack.sourceforge.io/
   ```

2. **Download Rainbow Tables**
   - Visit the OphCrack website to download free rainbow tables
   - Tables available: Vista Free, XP Free (limited coverage)
   - Commercial tables available for better coverage

3. **Install Rainbow Tables**
   - Extract downloaded tables to a directory
   - Configure OphCrack to point to the tables directory

4. **For LiveCD Method**
   - Download OphCrack LiveCD ISO
   - Burn to CD/DVD or create bootable USB
   - Boot target system from media

## Usage Examples and Common Commands

### Basic Workflow

1. **Launch OphCrack**
   ```bash
   ophcrack
   ```

2. **Load Hashes**
   - **From SAM file**: Load → Local SAM (requires admin privileges)
   - **From file**: Load → PWDUMP file (import previously dumped hashes)
   - **Manual entry**: Load → Single hash

3. **Install Rainbow Tables**
   - Tables → Install → Select table directory
   - Choose appropriate tables for hash type

4. **Start Cracking**
   - Click "Crack" button
   - Monitor progress in real-time
   - Results display cracked passwords

### Common Use Cases

**Scenario 1: Crack Local Windows Passwords**
```bash
# Run OphCrack with GUI (as root/admin)
sudo ophcrack

# Load → Local SAM
# Tables → Install (select rainbow tables)
# Click "Crack"
```

**Scenario 2: Crack from Exported Hash File**
```bash
# First, export hashes using pwdump or fgdump
# Then load in OphCrack:
# Load → PWDUMP file → select file
# Tables → Install
# Click "Crack"
```

**Scenario 3: Using OphCrack LiveCD**
```
1. Boot target machine from OphCrack LiveCD
2. OphCrack automatically launches
3. It detects and loads SAM file
4. Automatically starts cracking with included tables
5. View results on screen
```

**Scenario 4: Command-Line Usage**
```bash
# Crack hashes from file
ophcrack -g -d /path/to/tables -t table1:table2 -f hashfile.txt

# Options:
# -g : disable GUI
# -d : directory containing tables
# -t : specify tables to use
# -f : hash file to crack
```

## Links to Official Documentation and Tutorials

- **Official Website**: https://ophcrack.sourceforge.io/
- **Download Page**: https://ophcrack.sourceforge.io/download.php
- **Rainbow Tables**: https://ophcrack.sourceforge.io/tables.php
- **Documentation**: https://ophcrack.sourceforge.io/documentation.php
- **GitHub Repository**: https://gitlab.com/objectifsecurite/ophcrack
- **Tutorial Videos**: Search "OphCrack tutorial" on YouTube
- **Kali Linux Tools**: https://www.kali.org/tools/ophcrack/

## Tips & Tricks for Competition Scenarios

### Quick Wins

1. **Use LiveCD for Speed**
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
   - Switch to Hashcat for remaining hashes
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

### Competition Checklist

- [ ] OphCrack installed and tested
- [ ] Rainbow tables downloaded and configured
- [ ] LiveCD ISO ready on bootable media
- [ ] Backup hash extraction tools (pwdump, fgdump)
- [ ] Alternative cracking tools ready (Hashcat)
- [ ] Know the target Windows version
- [ ] Practice full workflow before competition
