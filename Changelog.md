### Changelog - ForgePDF

## Version 1.01 (2025-11-19)

### 🔧 Critical Fixes
- **Fixed PDF Trailer Issue**: Implemented missing `_puttrailer()` method that was causing PDF validation failures
- **Fixed PDF Structure**: Restored proper FPDF closing sequence following the correct order:
  - `_putpages()`
  - `_putresources()`
  - `_putinfo()`
  - `_putcatalog()`
  - `_putxref()`
  - `_puttrailer()`
  - `_enddoc()`
- **Fixed Content References**: Corrected `/Contents` object references in `_putpage()` method
- **Fixed Page Object Ordering**: Restored proper page content writing sequence

### 🚀 Improvements
- **Enhanced Output Methods**: Improved `Outpute()` method to handle both file mode and compatibility mode
- **Better Error Handling**: Added proper file handle checks to prevent runtime errors
- **Cross-Reference Table**: Implemented complete xref table with proper Size, Root, and Info references
- **PDF Validation**: All generated PDFs now pass standard PDF validators and work correctly with PDF reading APIs

### 🔍 What was fixed
- PDF files showing blank content in viewers
- "Unable to load page tree" errors in PDF APIs
- "Truncated file" warnings in PDF validators
- Incorrect page counting in PDF readers
- Missing trailer section causing PDF corruption
- Invalid cross-reference table entries

### ✅ Tested
- Simple PDF generation
- Complex text with special characters and bullets  
- Table generation with ForgePDFTab
- Both file mode (with `Open()`) and compatibility mode
- PDF validation with external tools

---

## Version 1.00 (2024-10-29)

#### New Features
- **ForgePDF Class**: A customized FPDF extension for handling PDF generation with enhanced file management and improved image handling.
- **Image Processing**: Now supports automatic identification and processing of image types (GIF, JPEG, PNG), providing better error handling for unsupported or missing image files.
- **UTF-8 Text Conversion**: Added `convertText` function to facilitate UTF-8 to Windows-1252 conversion for seamless text handling in PDFs.

#### Fixes
- **Error Handling**: Enhanced error reporting for file creation and image loading issues.
- **Page Management**: Improved `_putpage` and `_putpages` functions for accurate page linking and resource management in multi-page documents.
- **File Output Stability**: Adjustments in `_put` and `_putimages` methods to ensure images and pages are properly written to the PDF file without data loss.

#### Improvements
- **Session Management**: Updated `_putpages` function for consistent page root tracking and improved memory efficiency by discarding unnecessary page data.
- **Transparency Support**: Integrated transparency group support within pages, optimizing the handling of alpha layers for advanced graphic requirements.
- **File Header Control**: Improved `_putheader` functionality to confirm header information is written only once per document output.

#### Technical Updates
- **PHP Compatibility**: Tested and compatible with PHP 5.3, leveraging native file handling for cross-compatibility.
- **Image Parsing**: Enhanced `_parsegif`, `_parsejpg`, and `_parsepng` methods for a more robust PDF generation experience.

#### Known Issues
- **Image Style Preservation**: While the class supports basic image embedding, styling and advanced formatting of DOCX to PDF conversions may require additional tools, as raised in recent discussions.
