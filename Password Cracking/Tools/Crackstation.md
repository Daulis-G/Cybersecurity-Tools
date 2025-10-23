# CrackStation

## Overview
CrackStation is a free online password hash cracking service that uses massive pre-computed lookup tables (rainbow tables) to crack password hashes. It supports multiple hash types and can crack hashes in seconds that would take hours or days with traditional brute-force methods. CrackStation is particularly useful for quick lookups of common password hashes.

## Features
- **Free Online Service**: No installation required, accessible via web browser
- **Massive Rainbow Tables**: Uses pre-computed tables containing billions of hashes
- **Multiple Hash Types**: Supports LM, NTLM, md2, md4, md5, md5(md5_hex), md5-half, sha1, sha224, sha256, sha384, sha512, ripeMD160, whirlpool, MySQL 4.1+ (sha1(sha1_hex))
- **Fast Results**: Returns results in seconds for hashes in the database
- **Batch Processing**: Can crack multiple hashes simultaneously (up to 20 at once)
- **No Registration Required**: Simple paste-and-crack interface
- **Salt Detection**: Identifies when hashes contain salts (which cannot be cracked via rainbow tables)

## How to Use

### Basic Usage
1. Navigate to https://crackstation.net/
2. Paste your hash(es) into the text field (one per line, up to 20)
3. Complete the CAPTCHA verification
4. Click "Crack Hashes"
5. View results showing cracked passwords or "Not found" status

### Tips for Best Results
- Ensure hashes are properly formatted (no extra spaces or characters)
- Use the correct hash type - CrackStation auto-detects most formats
- For multiple hashes, separate each with a newline
- Check if your hash includes a salt (CrackStation will notify you if detected)

### Example
```
Input: 5f4dcc3b5aa765d61d8327deb882cf99
Output: password
```

## Pros
- **Speed**: Extremely fast for hashes in the database (seconds vs hours/days)
- **Ease of Use**: Simple web interface, no technical knowledge required
- **No Installation**: Web-based tool, works on any device with a browser
- **Free**: Completely free service with no account required
- **Large Database**: Billions of pre-computed hashes covering common passwords
- **Multiple Format Support**: Handles many different hash algorithms
- **Educational Value**: Great for learning about hash functions and password security

## Cons
- **Limited to Database**: Can only crack hashes that exist in pre-computed tables
- **No Custom Options**: Cannot specify custom wordlists or rules
- **Salted Hashes**: Cannot crack hashes with salts (by design of rainbow tables)
- **Uncommon Passwords**: Fails on unique or highly complex passwords not in database
- **Batch Limit**: Maximum of 20 hashes per request
- **Internet Required**: Requires active internet connection
- **Privacy Concerns**: Uploading hashes to third-party service (avoid sensitive/production hashes)

## Use Cases

### Penetration Testing
- Quick validation of captured password hashes
- Testing password strength in security assessments
- Demonstrating weak password vulnerabilities to clients

### Digital Forensics
- Recovering passwords from forensic investigations
- Analyzing compromised password databases
- Quick triage of hash types and values

### Security Research
- Analyzing leaked password databases
- Studying common password patterns
- Password strength research

### CTF Challenges
- Quick hash cracking in Capture The Flag competitions
- Verifying solutions to cryptography challenges

## Tips and Best Practices

1. **Verify Hash Format**: Ensure your hash is clean (no extra characters, proper length)
2. **Try Common Hashes First**: CrackStation works best with unsalted, common password hashes
3. **Use as First Step**: Start with CrackStation before investing time in offline cracking
4. **Combine with Other Tools**: If CrackStation fails, move to HashCat or John the Ripper
5. **Check Hash Type**: Make sure you know what type of hash you're working with
6. **Respect Legal Boundaries**: Only crack hashes you have permission to crack
7. **Don't Upload Sensitive Hashes**: Avoid using CrackStation for production or sensitive systems
8. **Understand Limitations**: Rainbow tables cannot crack salted hashes or very unique passwords

## Common Scenarios

### When CrackStation Works Well:
- Unsalted MD5, SHA1, SHA256 hashes
- Common passwords ("password123", "qwerty", etc.)
- Dictionary words and simple variations
- Leaked database hashes (if passwords were common)

### When to Use Alternative Tools:
- Salted hashes (use HashCat or John the Ripper)
- Complex, unique passwords
- When you need custom wordlists or rules
- When you need offline cracking for privacy
- Enterprise password policies with high complexity

## Related Tools
- **HashCat**: For advanced, offline password cracking with custom rules
- **John the Ripper**: For versatile password cracking with multiple modes
- **Ophcrack**: Specialized for Windows password cracking
- **Online Hash Databases**: hashes.com, HashKiller, OnlineHashCrack

## Resources
- Official Website: https://crackstation.net/
- Crackstation's Guide: https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm
- Hash Type Identification: https://hashcat.net/wiki/doku.php?id=example_hashes
