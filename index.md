---
layout: default
---

# About KicomAV

***


KicomAV is an open source (GPL v2) antivirus engine designed for detecting malware and disinfecting it. In fact, Since 1995, it has been written in C/C++ and it was integrated into the ViRobot engine of [HAURI](http://www.hauri.co.kr), 1998. I decided to re-create a new KicomAV. So, this is developed in Python. Anyone can participate in the development easily.

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/In-YnHDyDbk' frameborder='0' allowfullscreen></iframe></div>

## 1. How to use

***

### Requirements

* Python 2.7
* [pylzma](https://github.com/fancycode/pylzma)
* [yara](https://github.com/plusvic/yara)
* [backports.lzma](https://github.com/peterjc/backports.lzma)


### Quick start

* Three quick start options are available:
    * [Download the latest release](https://github.com/hanul93/kicomav/archive/master.zip) and unzip it.
    * Clone the repo: ```git clone git://github.com/hanul93/kicomav.git```.
    * Build KicomAV Engine & Plugins modules : ```build.sh build``` or ```build.bat build```
    * You can see ```Release``` Directory. Change the ```Release``` directory and run ```k2.py```.
    * You can update the latest signature. Run ```k2.py --update```.

## 2. Releases

***

### v0.30 (May 07, 2018)

* **Engine :**
  * k2engine: Changed WindowsError exception handling to OSError exception handling
  * k2engine: Modified Checking for malicious code to stop immediately via Ctrl+C
  * k2file: Changed WindowsError exception handling to OSError exception handling
  * k2file: Moved the path of the temporary folder

* **Plugins Modules :**
  * adware: Modified the data processing byte number in the ASN.1 parser
  * cryptolib: Supported crc32
  * dde: Changed malware pattern
  * hwp: Added Exploit.JS.Agent.gen check function
  * kavutil: Added malicious code pattern handling function of virus type
  * kavutil: Fixed the error handling part of malicious code pattern number
  * macro: Supported 32/64bit
  * nsis: Improved decompression speed
  * ole: Added CVE-2012-0158 pattern
  * ole: Fixed infinite loop error during parsing
  * pe: Supported 32/64bit
  * pe: Added error handling for invalid resource size
  * rtf: Added objdata extraction function
  * rtf: Changed malicious code patterns
  * upx: Fixed infinite loop error
  * ve: New support (scan for malware of virus types)

* **Command Line Interface :**
  * k2: Added color mode in Linux/Mac
  * k2: Fixed an error when updating k2.exe from a folder where k2.exe does not exist (# 1455)
  * k2: Fixed do not download k2.exe on platforms other than windows

### v0.29 (Jan 08, 2018)

* **Engine :**
  * k2engine: Handling the callback function call if the plugin module fails to load
  * k2engine: Processing to render the result of recompression in detail after malicious code in the compressed file is processed
  * k2engine: Fixed the problem that the extension can not be removed properly if the kmd file path name has a period (.)
  * k2engine: Fixed an infinite loop problem in case of malfunction code failure
  * k2engine: Process temporary folders by process
  * k2file: Add a class to process temporary folders by process

* **Plugins Modules :**
  * adware: new support
  * attach: process to add size information of an attached image to newly extract an attached image
  * bz: New support
  * carch: New support
  * dde: New support
  * egg: new support
  * elf: verbose processing on ELF 64bit
  * emalware: Handle MD5 calculations if section size is 0
  * emalware: Handle malicious code in addition to .text area
  * gz: New support
  * kavutil: MD5 pattern is compressed so that it is decompressed and then loaded
  * ole: Added malicious code remedy to infected ole file
  * ole: Correct the processing for bad access and the PPS length to be 0x40 max.
  * ole: Eliminate unnecessary logic
  * ole: Exploit.OLE.CVE-2003-0347 Add inspection logic
  * ole: Opening ole file in write mode to handle failure to delete stream
  * olenative: Added malicious code remediation to Ole10Native files
  * pdf: Add malware PDF signature test signature
  * pdf: Added Trojan.PDF.Generic inspection logic
  * pdf: Improved inspection speed by avoiding unnecessary stream extraction
  * pe: Do not calculate MD5 if section size is 0
  * pe: Error handling to divide by 0 in converting RAV to Offset
  * pe: If there is a digital signature, the position and size of the attached image are newly processed
  * pe: Processing parsing failure if there is not enough data in the .rsrc area
  * pyz: Added pyc type malicious code
  * pyz: Improved error by checking TOC type
  * pyz: New support
  * tar: New support
  * unpack: Exceptions when zlib is not a compressed object
  * unpack: Process zlib and embed_ole simultaneously to recognize format
  * unpack: add infected malicious code remedy to embed ole file
  * upx: Add exception handling for uncompressed sizes
  * upx: Fixed an issue where execution compression was not released
  * xz: New support
  * yaraex: Engine initialization failure processing when there is no yara module

* **Command Line Interface :**
  * k2: engine initialization failure processing when there is no yara module
  * k2: Processing to prevent the same malicious code inspection result from being output
  * k2: Easily recognizable by adding a comma (,) to the number of malicious code patterns loaded
  * k2: Outputs error message after processing residual printout when nonexistent Paht check
  * k2: Output the plug-in module that failed to load as an error message
  * k2: Processing to render the result of recompression in detail after malicious code in the compressed file is processed
  * k2: Processing to prevent redundant output when expressing the result of re-compression in detail
  * k2: Change the update file to a gz file and process the update itself
  * k2: Change update path
    * Related Issue: https://github.com/hanul93/kicomav/issues/4
  * k2: Fixed error when scrolling while printing Windows 10 legacy console
    * Related Issue: https://github.com/hanul93/kicomav/issues/7

* **Tools :**
  * sigtool_md5: Reduce capacity by compressing MD5 pattern
  * sigtool_md5: Prevent duplicate malware name generation
  * sigtool_yar: New support

### 0.28 (Sep 4, 2017)

* Improved decompression speed of compressed files
* Added resource parsing function for PE file
* Added malware scanning function using YARA rule
* Fixed product hang when extracting ZIP files with errors
* Fixed errors when scanning ZIP and HWP files with passwords

### 0.27b (May 22, 2017)

* Fixed for pylzma import error

### 0.27a (May 17, 2017)

* Enabled update option (--update)

### 0.27 (May 4, 2017)

* Redesigned an architecture of KicomAV

### 0.26 (June 16, 2016)

* Added support for decompressed BinData/BIN0001.OLE in HWP File
* Added support for decompressed OleNative in OLE File
* Added support for scanning the malware for APK(Android) files

### 0.25 (July 18, 2013)

* Added support for decompressed UPX file
* Added support for separated the attached files from PE file
* Added support for scannning the malware for Common Object File Format (COFF)

### 0.24 (July 7, 2013)

* Added support for decompressed ALZ file
* Added support for decompressed EGG file
* Added support for scanning the malware for MSWord and MSExcel files

### 0.23 (June 27, 2013)

* Added support for scanning the malware for PE file
* Added support for multi scan paths
* Added display for the signature number and the last update information
* BUGFIX : infinite loop in OLE PPS Dump

### 0.22 (June 16, 2013)

* Added support for decompressed OLE file
* Added support for scanning the exploit code for Hangul Word Processor (HWP) file

### 0.21 (June 11, 2013)

* Added support for command option for archive files
* Added support for decompressed ZIP file

### 0.20b (June 1, 2013)

* Added support for command line : k2.py

### 0.20 (May 27, 2013)

* Redesigned Plug-in architectures

### 0.10 (May 8, 2013)

* Initial release


## 3. Supporters

***

![](/images/support.png)