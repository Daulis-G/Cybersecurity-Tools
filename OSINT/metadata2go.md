## [Metadata2Go](https://www.metadata2go.com)

### Tool Name and Brief Description
Metadata2Go is a free, browser-based online tool for extracting, viewing, and removing hidden metadata from various file types including images (JPEG, PNG, GIF, TIFF), documents (PDF, DOCX, XLSX, PPTX), audio files (MP3, WAV), and video files. It provides instant access to EXIF data, GPS coordinates, camera information, creation/modification timestamps, author details, and software fingerprints without requiring any software installation. This makes it invaluable for OSINT investigations, digital forensics, privacy auditing, and cybersecurity competitions where rapid metadata analysis is crucial.

### Installation Instructions
**Dependencies:**
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection
- JavaScript enabled
- No software installation required (browser-based tool)

**Alternative CLI Tools (for offline/advanced usage):**

**ExifTool (recommended for competitions):**
```bash
# Linux/Ubuntu:
sudo apt-get install libimage-exiftool-perl

# macOS:
brew install exiftool

# Windows:
# Download from https://exiftool.org/
# Or use Chocolatey:
choco install exiftool
```

**Metadata Extraction Library (Python):**
```bash
pip install pillow  # For image EXIF
pip install PyPDF2  # For PDF metadata
pip install mutagen # For audio metadata
```

**Setup:**
1. Navigate to https://www.metadata2go.com
2. Tool is immediately ready to use
3. No registration or account creation required
4. Files processed locally in browser (privacy-friendly)

### Usage Examples and Common Commands

**Web Interface Workflow:**
1. **Select file** - Click "Choose File" or drag & drop
   - Supported: Images, PDFs, Office docs, audio/video files
   - Max file size: typically 10-50 MB (varies by file type)

2. **View Metadata** - Tool automatically extracts:
   - **EXIF Data** - Camera model, settings, lens info
   - **GPS Coordinates** - Latitude, longitude, altitude
   - **Timestamps** - Creation, modification, access dates
   - **Software** - Programs used to create/edit file
   - **Author Info** - Creator name, organization, copyright
   - **Device Info** - Phone model, OS version

3. **Download Report** - Export metadata as text file

4. **Remove Metadata** - Strip all metadata for privacy

**Command-Line ExifTool (for competitions):**

**Basic Extraction:**
```bash
# Extract all metadata
exiftool image.jpg

# Extract GPS coordinates only
exiftool -gps:all image.jpg

# Extract timestamps
exiftool -CreateDate -ModifyDate -DateTimeOriginal image.jpg

# Extract camera/device info
exiftool -Make -Model -Software image.jpg
```

**Advanced Searches:**
```bash
# Find all images with GPS data in directory
exiftool -filename -gpsposition -ext jpg -r .

# Extract metadata from all files recursively
exiftool -r -csv . > metadata_report.csv

# Search for specific software used
exiftool -if '$Software =~ /photoshop/i' -filename -r .

# Find images from specific camera
exiftool -if '$Model eq "iPhone 12 Pro"' -filename -r .
```

**Metadata Removal:**
```bash
# Remove all metadata from image
exiftool -all= image.jpg

# Remove GPS data only
exiftool -gps:all= image.jpg

# Strip metadata from all images in folder
exiftool -all= *.jpg
```

**Common OSINT Use Cases:**
- Track photo location from GPS coordinates
- Identify camera/phone model to profile target
- Extract timestamps to build timeline of events
- Discover author/creator information from documents
- Find software version vulnerabilities
- Correlate metadata across multiple files
- Verify image authenticity (editing detection)
- Recover deleted/hidden metadata

### Links to Official Documentation and Tutorials

**Official Resources:**
- **Metadata2Go Tool:** https://www.metadata2go.com
- **EXIF Standard:** https://en.wikipedia.org/wiki/Exif
- **ExifTool Official Site:** https://exiftool.org/
- **ExifTool Documentation:** https://exiftool.org/exiftool_pod.html

**EXIF/Metadata Guides:**
- **EXIF Tags Reference:** https://exiftool.org/TagNames/EXIF.html
- **GPS Tag Reference:** https://exiftool.org/TagNames/GPS.html
- **Metadata Extraction Guide:** https://www.sans.org/blog/metadata-analysis-for-digital-forensics/
- **Image Forensics Tutorial:** https://29a.ch/photo-forensics/

**Privacy & Security:**
- **Metadata Privacy Risks:** https://www.eff.org/issues/privacy
- **OSINT Framework (Metadata):** https://osintframework.com/

**Video Tutorials:**
- **ExifTool Tutorial:** https://www.youtube.com/results?search_query=exiftool+tutorial
- **Image Metadata Analysis:** https://www.youtube.com/results?search_query=image+metadata+osint

### Tips & Tricks for Competition Scenarios

1. **GPS Coordinate Extraction:**
   - Copy GPS coordinates from Metadata2Go
   - Paste directly into Google Maps for location
   - Format: `51.5074° N, 0.1278° W` or decimal degrees
   - Use reverse geocoding services for address

2. **Timestamp Analysis:**
   - Compare `CreateDate` vs `ModifyDate` to detect edits
   - `DateTimeOriginal` is hardest to manipulate
   - Timezone info (`OffsetTime`) reveals location
   - Gaps in sequence suggest deleted photos

3. **Camera/Device Fingerprinting:**
   - Same device = related images/person
   - Phone model reveals economic status, time period
   - Serial numbers can uniquely identify device
   - Software version shows update habits

4. **Hidden Author Information:**
   - PDFs often contain creator name and organization
   - Office docs leak computer usernames
   - Check `Author`, `Creator`, `Producer` fields
   - Company names in metadata reveal affiliations

5. **Software Analysis:**
   - Photo editing software presence = manipulation
   - Specific apps reveal technical skill level
   - Version numbers help date the file
   - Chain of software shows editing history

6. **Metadata Correlation:**
   - Cross-reference metadata across multiple files
   - Same GPS location = related photos
   - Sequential timestamps = event reconstruction
   - Matching device IDs = single source attribution

7. **Privacy Leaks in Documents:**
   - Corporate PDFs leak employee names, roles
   - Internal file paths reveal directory structure
   - Template names show document workflow
   - Comments/revisions contain sensitive data

8. **Competition Speed Techniques:**
   - Bookmark Metadata2Go for instant access
   - Use browser DevTools to automate form submission
   - Keep ExifTool installed for offline analysis
   - Create bash aliases for common ExifTool commands
   - Pre-prepare GPS coordinate converter bookmarks

9. **Bulk Analysis Workflow:**
   ```bash
   # Create CSV report of all images
   exiftool -csv -r -ext jpg -ext png . > analysis.csv
   
   # Import into spreadsheet for filtering/sorting
   # Filter by GPS, date ranges, device models
   ```

10. **Detect Metadata Manipulation:**
    - Inconsistent timestamps (create date after modify date)
    - Missing expected EXIF fields for camera model
    - GPS coordinates outside plausible range
    - Software field shows metadata editor (e.g., exiftool)

11. **Social Media Metadata:**
    - Most platforms strip EXIF (Facebook, Instagram, Twitter)
    - Try to obtain original file from source
    - LinkedIn PDFs sometimes retain author info
    - Screenshot metadata shows when/how captured

12. **Geolocation Triangulation:**
    - Multiple images with GPS = movement pattern
    - Combine with timestamp = speed/travel analysis
    - Use Google Earth timeline features
    - Correlate with known events/locations

13. **Thumbnail Extraction:**
    ```bash
    # Extract embedded thumbnail (may show original)
    exiftool -b -ThumbnailImage image.jpg > thumb.jpg
    
    # Compare thumbnail to main image for edits
    ```

14. **Audio/Video Metadata:**
    - Recording device info from audio files
    - Video encoding software and settings
    - Duration, bitrate, codec reveal authenticity
    - GPS from phone-recorded videos

15. **Document Metadata Extraction:**
    ```bash
    # PDF metadata
    exiftool document.pdf
    
    # Office documents
    exiftool report.docx
    
    # Look for: Author, Company, Created date, Modified by
    ```

16. **Browser Integration:**
    - Right-click file → Properties (Windows) shows basic metadata
    - macOS Preview → Tools → Show Inspector
    - Quick pre-check before deeper analysis

17. **Metadata as Evidence Chain:**
    - Document chain of custody in competitions
    - Screenshot metadata extraction process
    - Save raw ExifTool output as proof
    - Note any anomalies or red flags

18. **Privacy Protection (defensive):**
    - Always strip metadata before sharing competition files
    - Use `exiftool -all=` or Metadata2Go removal feature
    - Check files teammates share for leaks
    - Educate team on metadata risks

19. **Combine with Other OSINT:**
    - GPS coordinates → Google Street View for visual context
    - Timestamps → timezone conversion → local time analysis
    - Camera model → price point → socioeconomic profiling
    - Software used → skill level assessment
    - Phone model → carrier lookup (if IMEI visible)

20. **Common Competition Pitfalls:**
    - Not checking multiple metadata fields (focus on GPS alone)
    - Ignoring timezone offsets (wrong time interpretation)
    - Assuming metadata is authentic (can be forged)
    - Missing thumbnail/preview metadata
    - Not correlating across file sets
