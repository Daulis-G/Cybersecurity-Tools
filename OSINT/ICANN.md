## [ICANN Lookup](https://lookup.icann.org/en/lookup)

ICANN Lookup (WHOIS/RDAP) is an official domain registration data query service provided by the Internet Corporation for Assigned Names and Numbers (ICANN). This tool enables users to search domain name registration details using both the legacy WHOIS protocol and the modern Registration Data Access Protocol (RDAP). It provides real-time access to domain registrar information, ownership details, contact information, registration dates, expiration dates, and DNS server information. This makes it essential for OSINT investigations involving domain research, cybersecurity threat analysis, fraud investigation, and digital footprint analysis.

---

**Requirements:**
- Web browser (Chrome, Firefox, Safari, Edge)
- Internet connection
- No software installation required (browser-based tool)

**Setup:**
1. Navigate to https://lookup.icann.org/en/lookup
2. The tool is immediately ready to use

---

## Usage Examples and Common Commands

**Basic Workflow:**
1. **Enter domain name** - Type target domain (e.g., example.com)
2. **Submit query** - Click search button
3. **Review results** - Analyze:
   - Registrar information
   - Registration dates (created, updated, expires)
   - Registrant details (if not privacy-protected)
   - Name servers
   - Domain status codes

**Common Use Cases:**
- Investigate suspicious domains for phishing campaigns
- Identify domain ownership and registration patterns
- Track domain expiration dates for takeover monitoring
- Gather contact information for abuse reporting
- Correlate domains registered by the same entity
- Verify domain legitimacy for security assessments
- Monitor DNS changes and name server updates

---

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
2. **Domain status codes matter:** Understanding EPP status codes helps identify locked, pending transfer, or held domains
3. **Look for patterns:** Multiple domains with same registrant email/name server often indicate related infrastructure
4. **Check registration dates:** Newly registered domains are higher risk for phishing/malware campaigns
5. **Monitor name server changes:** DNS modifications can indicate domain hijacking or infrastructure changes
6. **Note registrar information:** Some registrars are commonly abused for malicious domains
7. **Privacy vs. transparency:** Domains using privacy protection may warrant additional scrutiny
8. **Expiration tracking:** Expired domains can be re-registered by attackers for typosquatting
