## [Pretty Good Privacy (PGP)](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)
Permalink: [Pretty Good Privacy (PGP)](#pretty-good-privacy-pgphttpsenwikipediaorgwikipretty_good_privacy)

PGP (Pretty Good Privacy) is a cryptographic system used for encrypting and signing data, ensuring secure communication and verifying authenticity. PGP Lookup refers to public keyserver databases that allow users to search for, retrieve, and verify public PGP keys associated with email addresses or user IDs. These keyservers enable OSINT researchers to discover email addresses, verify identities, track digital footprints, and investigate communication patterns. Public PGP keys often contain metadata like creation dates, email addresses, associated identities, and key signatures that can reveal relationships between individuals.

**Requirements:**
- Web browser (for online keyserver lookups)
- Internet connection

**Setup:**
1. Navigate to a public PGP keyserver:
   - http://keyserver.ubuntu.com/
   - http://keys.openpgp.org/
   - http://pgp.mit.edu/
2. The tool is immediately ready to use

## Usage Examples and Common Commands
Permalink: [Usage Examples and Common Commands](#usage-examples-and-common-commands)

**Basic Workflow:**
1. **Navigate to keyserver** - Choose from Ubuntu Keyserver, OpenPGP, or MIT PGP
2. **Enter search query** - Input email address, key ID, or name
3. **Review results** - Examine:
   - Public keys associated with the query
   - Email addresses in key metadata
   - Key creation dates and expiration
   - User IDs (UIDs) and signatures
   - Key fingerprints for verification

**Common Use Cases:**
- Discover email addresses associated with a target
- Find alternative identities/usernames in key metadata
- Track key creation dates to establish timeline
- Identify relationships through key signatures
- Verify authenticity of communications
- Investigate developer identities in open-source projects
- Correlate keys across different platforms

### Links to Official Documentation and Tutorials
Permalink: [Links to Official Documentation and Tutorials](#links-to-official-documentation-and-tutorials)

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
Permalink: [Tips & Tricks for Competition Scenarios](#tips--tricks-for-competition-scenarios)

1. **Email Discovery:** PGP keys often contain multiple email addresses (UIDs) - search by partial names to find all associated keys and look for typo variations or similar names
2. **Key Signatures:** Check who signed a key to identify trusted relationships and professional/social networks
3. **Metadata Analysis:** Key creation dates can establish when someone started using PGP, revealing activity timelines
4. **Cross-Platform Search:** Try multiple keyservers as they may have different keys or metadata for the same person
5. **Historical Data:** Some keyservers retain old/revoked keys - useful for tracking identity changes or compromised keys
6. **Developer Investigation:** Many open-source developers publish keys - link GitHub commits to real identities
7. **Username Correlation:** Key comments and UIDs often contain usernames used on other platforms
8. **Email Pattern Recognition:** Look for organizational email patterns (firstname.lastname@company.com) to identify other employees
