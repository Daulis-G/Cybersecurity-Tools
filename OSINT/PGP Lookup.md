## [Pretty Good Privacy (PGP)](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)

### Tool Name and Brief Description
PGP (Pretty Good Privacy) is a cryptographic system used for encrypting and signing data, ensuring secure communication and verifying authenticity. PGP Lookup refers to public keyserver databases that allow users to search for, retrieve, and verify public PGP keys associated with email addresses or user IDs. These keyservers enable OSINT researchers to discover email addresses, verify identities, track digital footprints, and investigate communication patterns. Public PGP keys often contain metadata like creation dates, email addresses, associated identities, and key signatures that can reveal relationships between individuals.

### Installation Instructions
**Dependencies:**
- Web browser (for online keyserver lookups)
- GnuPG (GPG) software for local key management
- Internet connection

**Installing GPG Tools:**

**Linux (Debian/Ubuntu):**
```bash
sudo apt-get update
sudo apt-get install gnupg
```

**macOS:**
```bash
# Using Homebrew
brew install gnupg

# Or download GPG Suite from https://gpgtools.org/
```

**Windows:**
```bash
# Download Gpg4win from https://gpg4win.org/
# Or use Windows Package Manager
winget install GnuPG.Gpg4win
```

**Verification:**
```bash
gpg --version
```

### Usage Examples and Common Commands

**Web-Based Keyserver Lookups:**
1. Navigate to a public keyserver:
   - http://keyserver.ubuntu.com/
   - http://keys.openpgp.org/
   - http://pgp.mit.edu/
2. Enter search query (email address, key ID, or name)
3. Review results for public keys, email addresses, and metadata

**Command-Line GPG Operations:**

**Searching for Keys:**
```bash
# Search by email
gpg --keyserver keyserver.ubuntu.com --search-keys user@example.com

# Search by name
gpg --keyserver keys.openpgp.org --search-keys "John Doe"

# Search by key ID
gpg --keyserver pgp.mit.edu --search-keys 0x1234ABCD
```

**Importing Keys:**
```bash
# Import key from keyserver
gpg --keyserver keyserver.ubuntu.com --recv-keys 0x1234ABCD

# Import key from file
gpg --import publickey.asc
```

**Viewing Key Information:**
```bash
# List all public keys in keyring
gpg --list-keys

# Show detailed key information
gpg --fingerprint user@example.com

# Export public key
gpg --armor --export user@example.com > key.asc
```

**Verifying Signatures:**
```bash
# Verify a signed file
gpg --verify document.sig document.txt

# Check key signatures (web of trust)
gpg --list-sigs user@example.com
```

**Common OSINT Use Cases:**
- Discover email addresses associated with a target
- Find alternative identities/usernames in key metadata
- Track key creation dates to establish timeline
- Identify relationships through key signatures
- Verify authenticity of communications
- Investigate developer identities in open-source projects
- Correlate keys across different platforms

### Links to Official Documentation and Tutorials

**PGP Keyservers:**
- **Ubuntu Keyserver:** http://keyserver.ubuntu.com/
- **OpenPGP Keyserver:** http://keys.openpgp.org/
- **MIT PGP Keyserver:** http://pgp.mit.edu/
- **SKS Keyserver Network:** https://sks-keyservers.net/

**Official Documentation:**
- **GnuPG Official Site:** https://gnupg.org/
- **GnuPG Documentation:** https://gnupg.org/documentation/
- **GPG Manual:** https://www.gnupg.org/gph/en/manual.html
- **PGP Wikipedia:** https://en.wikipedia.org/wiki/Pretty_Good_Privacy
- **OpenPGP Standard:** https://www.openpgp.org/

**Tutorials:**
- **GPG Quickstart Guide:** https://gnupg.org/gph/en/manual/c14.html
- **Email Encryption Tutorial:** https://emailselfdefense.fsf.org/
- **Key Signing Party Guide:** https://www.debian.org/events/keysigning
- **GPG Best Practices:** https://riseup.net/en/security/message-security/openpgp/best-practices

### Tips & Tricks for Competition Scenarios

1. **Email Discovery:**
   - PGP keys often contain multiple email addresses (UIDs)
   - Search by partial names to find all associated keys
   - Look for typo variations or similar names
   - Check key comments for additional information

2. **Metadata Mining:**
   - Key creation dates reveal when person became security-conscious
   - Expiration dates show activity/awareness levels
   - Key type/size indicates technical sophistication
   - Sub-keys show compartmentalization practices

3. **Signature Analysis (Web of Trust):**
   - View who has signed a key: `gpg --list-sigs <key-id>`
   - Signatures reveal social/professional connections
   - Mutual signatures indicate close relationships
   - Absence of signatures may indicate isolated/new user

4. **Username Correlation:**
   - Usernames in key IDs often match other platforms
   - Search username from PGP key on GitHub, forums, social media
   - Key comments sometimes contain handles or nicknames

5. **Historical Lookup:**
   - Use archive.org to check old keyserver snapshots
   - Keys may have been deleted but captured in archives
   - Historical versions show changes in identity/email

6. **Multiple Keyserver Strategy:**
   - Different keyservers may have different keys for same person
   - Try ubuntu, MIT, and openpgp.org for complete picture
   - Some keyservers federate, others are independent

7. **Advanced Search Techniques:**
   ```bash
   # Search multiple email patterns
   for domain in gmail.com yahoo.com hotmail.com; do
     gpg --keyserver keyserver.ubuntu.com --search-keys "@$domain"
   done
   
   # Extract all emails from a key
   gpg --list-keys --with-colons <key-id> | grep uid | cut -d: -f10
   ```

8. **GitHub/GitLab Integration:**
   - Developers often use PGP to sign commits
   - GitHub shows verified commits with key IDs
   - Search key ID on keyservers to find email/identity
   - Check `.gnupg` or `.gpg` in public repositories

9. **Competition Speed Tips:**
   - Bookmark keyserver URLs for quick access
   - Use browser search feature to find emails on keyserver results page
   - Create GPG aliases: `alias gpgs='gpg --keyserver keyserver.ubuntu.com --search-keys'`
   - Keep common commands in text file for copy-paste

10. **Photo IDs in Keys:**
    - Some PGP keys contain embedded photos
    - View photos: `gpg --list-options show-photos --list-keys <key-id>`
    - Photos can be extracted for reverse image search
    - Rare but valuable when found

11. **Revocation Investigation:**
    - Revoked keys indicate compromised/retired identities
    - Check revocation reasons: `gpg --list-keys --list-options show-unusable-uids`
    - May indicate security incident or identity change

12. **Dark Web Crossover:**
    - Many dark web users publish PGP keys for secure communication
    - Search dark web marketplace keys on public keyservers
    - Can link clearnet and dark web identities

13. **Key ID Format Recognition:**
    - Short key ID: 8 hex characters (0x1234ABCD)
    - Long key ID: 16 hex characters (0x1234ABCD5678EF90)
    - Fingerprint: 40 hex characters
    - Always use long format or fingerprint to avoid collisions

14. **Automation for Bulk Research:**
    ```bash
    # Bulk key lookup from email list
    cat emails.txt | while read email; do
      echo "Searching: $email"
      gpg --keyserver keyserver.ubuntu.com --search-keys $email 2>&1 | grep -i "pub\|uid"
      echo "---"
    done
    ```

15. **Cross-Reference with Other OSINT:**
    - Email from PGP → search in breach databases (Have I Been Pwned)
    - Username from PGP → search on Sherlock or WhatsMyName
    - Name from PGP → search on LinkedIn, company directories
    - Key creation date → correlate with account creation dates elsewhere
