# [CyberChef](https://gchq.github.io/CyberChef/)
A powerful web-based data analysis and transformation toolkit. CyberChef is often described as the "Cyber Swiss Army Knife" for carrying out encoding, decoding, encryption, decryption, compression, hashing, and data analysis operations directly in your browser.

---

Requirements:
- Modern web browser (Chrome, Firefox, Edge, Safari)
- No installation or account required
- JavaScript enabled
- Internet connection (for online version) or local deployment option available

Setup:
1. Navigate to https://gchq.github.io/CyberChef/ in your web browser
2. For offline use, download the standalone version from the GitHub repository
3. The interface loads automatically with three main sections: Operations, Recipe, and Input/Output
4. Start using immediately - no configuration needed

---

## Usage Examples and Common Commands

**Basic Workflow:**
1. Drag or paste data into the Input box
2. Search for operations in the Operations panel
3. Drag operations into the Recipe panel to build your workflow
4. Click "Bake" to execute the recipe (or enable Auto Bake)
5. View results in the Output box

**Key Operations:**
- **Magic**: Automatically detects encoding types and suggests decoding operations
- **From Base64/To Base64**: Decode or encode Base64 data
- **From Hex/To Hex**: Convert hexadecimal to text or vice versa
- **AES Decrypt/Encrypt**: Symmetric encryption operations
- **Extract Files**: Pull embedded files from data
- **Parse X.509 certificate**: Analyze SSL/TLS certificates
- **Entropy**: Measure randomness in data (useful for detecting encryption/compression)
- **XOR**: Apply XOR operations with various keys
- **Gunzip/Gzip**: Decompress or compress data
- **MD5/SHA1/SHA256**: Generate cryptographic hashes
- **ROT13**: Apply Caesar cipher rotation
- **URL Decode/Encode**: Handle URL encoding
- **Regular expression**: Extract or replace patterns
- **Strings**: Extract readable strings from binary data

**Common Use Cases:**
- Decode Base64-encoded payloads or files
- Analyze obfuscated JavaScript or PowerShell scripts
- Extract and decrypt malware command-and-control communications
- Parse and validate certificates, JWTs, or API tokens
- Convert between different data formats (hex, binary, ASCII)
- Chain multiple operations together (e.g., Base64 decode → Gunzip → Parse JSON)
- Use Magic operation for unknown encoding types
- Calculate file hashes for verification
- Deobfuscate competition challenge files

---

### Links to Official Documentation and Tutorials
- Official CyberChef Repository: https://github.com/gchq/CyberChef
- Live Instance: https://gchq.github.io/CyberChef/
- Wiki Documentation: https://github.com/gchq/CyberChef/wiki
- Operation Index: Available in-tool via search bar
- GCHQ Blog Post: https://www.gchq.gov.uk/news/cyberchef-the-cyber-swiss-army-knife

### Tips & Tricks for Competition Scenarios
1. Enable "Auto Bake" to see results in real-time as you build your recipe
2. Use the Magic operation first when dealing with unknown encoding or obfuscation
3. Save useful recipes using the "Save recipe" button for quick reuse
4. Use "Fork" feature to branch recipes and try different approaches
5. Press F1 while hovering over operations for quick help documentation
6. Chain multiple operations: many challenges require multiple decoding steps
7. Use the "Extract Files" operation to pull embedded files from hex dumps or Base64 blobs
8. Check Entropy to identify encrypted or compressed sections in data
9. Bookmark recipes by copying the URL - CyberChef encodes the recipe in the URL parameters
10. Use "From Hexdump" for analyzing memory dumps or packet captures
11. Remember that operations execute in order from top to bottom in the Recipe panel
12. Utilize the "Regular expression" operation to extract specific patterns from large data sets
13. Download the offline version for competitions with unreliable internet access
