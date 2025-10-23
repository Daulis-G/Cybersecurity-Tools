## [ICANN Lookup](https://lookup.icann.org/en/lookup)

### Tool Name and Brief Description
ICANN Lookup (WHOIS/RDAP) is an official domain registration data query service provided by the Internet Corporation for Assigned Names and Numbers (ICANN). This tool enables users to search domain name registration details using both the legacy WHOIS protocol and the modern Registration Data Access Protocol (RDAP). It provides real-time access to domain registrar information, ownership details, contact information, registration dates, expiration dates, and DNS server information. This makes it essential for OSINT investigations involving domain research, cybersecurity threat analysis, fraud investigation, and digital footprint analysis.

### Installation Instructions
**Dependencies:**
- Web browser (Chrome, Firefox, Safari, Edge)
- Internet connection
- No software installation required (browser-based tool)

**Alternative CLI Installation (for advanced users):**
```bash
# Install WHOIS command-line tool
# Linux/Ubuntu:
sudo apt-get install whois

# macOS:
brew install whois

# Windows (PowerShell):
# Built-in: Use Resolve-DnsName or online tools
```

**Setup:**
1. Navigate to https://lookup.icann.org/en/lookup
2. Tool is immediately ready to use
3. For CLI tools, no additional configuration needed

### Usage Examples and Common Commands
**Web Interface Workflow:**
1. **Enter domain name** - Type target domain (e.g., example.com)
2. **Submit query** - Click search button
3. **Review results** - Analyze:
   - Registrar information
   - Registration dates (created, updated, expires)
   - Registrant details (if not privacy-protected)
   - Name servers
   - Domain status codes

**Command-Line Examples:**
```bash
# Basic WHOIS lookup
whois example.com

# Query specific WHOIS server
whois -h whois.verisign-grs.com example.com

# Extract specific information
whois example.com | grep -i "creation date"
whois example.com | grep -i "registrar"
whois example.com | grep -i "name server"

# Bulk domain lookup (bash script)
for domain in $(cat domains.txt); do
  echo "Checking $domain"
  whois $domain | grep -i "creation date"
done
```

**Common Use Cases:**
- Investigate suspicious domains for phishing campaigns
- Identify domain ownership and registration patterns
- Track domain expiration dates for takeover monitoring
- Gather contact information for abuse reporting
- Correlate domains registered by same entity
- Verify domain legitimacy for security assessments
- Monitor DNS changes and name server updates

### Links to Official Documentation and Tutorials
- **ICANN Lookup Tool:** https://lookup.icann.org/en/lookup
- **ICANN WHOIS Policy:** https://www.icann.org/resources/pages/whois-2018-01-17-en
- **RDAP Protocol Specification:** https://www.icann.org/rdap
- **WHOIS Command Tutorial:** https://linux.die.net/man/1/whois
- **Domain Status Codes Guide:** https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en
- **WHOIS Privacy & GDPR:** https://www.icann.org/resources/pages/gtld-registration-data-specs-en
- **Registrar Lookup:** https://www.icann.org/registrar-reports/accredited-list.html

### Tips & Tricks for Competition Scenarios
1. **Check multiple sources:** ICANN Lookup may show limited data due to privacy protection - cross-reference with:
   - Regional registrars (ARIN, RIPE, APNIC)
   - Historical WHOIS databases (WhoisXML, DomainTools)
   - DNS lookup tools (dig, nslookup)

2. **Domain status codes matter:**
   - `clientTransferProhibited` - Domain locked from transfer
   - `pendingDelete` - Domain expiring soon (possible takeover)
   - `redemptionPeriod` - Recently expired (recovery window)
   - `serverHold` - Domain suspended (abuse/legal issues)

3. **Analyze registration patterns:**
   - Multiple domains registered same day = potential campaign
   - Short registration periods (1 year) = possible disposable domains
   - Privacy protection = legitimate or hiding identity?
   - Bulk registrations from same registrar = infrastructure mapping

4. **Name server analysis:**
   - Same NS across domains = related infrastructure
   - Use `dig NS example.com` to find authoritative servers
   - Look for patterns in hosting providers

5. **Registrar intelligence:**
   - Certain registrars popular with threat actors
   - "Bulletproof" hosting indicators
   - Registrar abuse contacts for reporting

6. **Historical lookups:**
   - WHOIS doesn't show history - use archive.org or paid tools
   - Look for ownership changes over time
   - Track when privacy protection was added

7. **Subdomain enumeration:**
   - WHOIS only shows main domain - use DNS enumeration for subdomains
   - Tools: Sublist3r, Amass, Certificate Transparency logs

8. **Email pattern recognition:**
   - Registrant emails (when visible) can link multiple domains
   - Search email addresses across other databases
   - Pattern: admin@domain vs. personal emails

9. **Expiration monitoring:**
   - Note expiration dates for domain squatting opportunities
   - Expired domains may be available for defensive registration
   - Monitor competitor/adversary domain renewals

10. **Rate limiting awareness:**
    - WHOIS servers rate-limit queries (typically 50-100/day)
    - Space out bulk lookups to avoid blocking
    - Use API services for large-scale investigations

11. **Privacy workarounds:**
    - If WHOIS data redacted, check:
      - Web archive snapshots (before privacy was enabled)
      - SSL certificate information (may contain org details)
      - Website contact pages or legal documents
      - LinkedIn/social media for domain administrators

12. **Competition shortcuts:**
    - Save WHOIS output to file: `whois domain.com > domain.txt`
    - Use grep/awk for quick filtering in terminal
    - Create aliases: `alias wi='whois'`
    - Combine with other OSINT: `whois $(dig +short example.com)`
