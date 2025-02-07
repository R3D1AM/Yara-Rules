# Yara-Rules

### A collection of Yara rules for malware scanning
==================================================================================

## TL;DR

- Install YARA and write or obtain rules.
- Use the `yara` command-line tool to scan files or directories.
- Optionally, automate the scanning process with scripts.

==================================================================================

# How to use:

This guide explains how to install and use YARA for scanning files and directories with custom or pre-defined rules. YARA is a powerful tool used for pattern matching, often utilized in malware detection and file analysis.

## 1. Install YARA

YARA is available for different platforms (Windows, Linux, macOS). You can install it using the package manager for your system or by compiling it from source.

### On Linux (Debian/Ubuntu-based systems)

```sudo apt update sudo apt install yara```

### On macOS (using Homebrew)

```brew install yara```

### On Windows

You can download the YARA installer from the official YARA GitHub repository:
- Go to: [YARA Releases on GitHub](https://github.com/VirusTotal/yara/releases)
- Download the Windows installer or a precompiled binary and follow the instructions.

Alternatively, if you use **Chocolatey**, you can install it via:

```choco install yara```

==================================================================================

## 2. Write or Obtain YARA Rules

YARA rules are written to identify patterns in files. You can create custom rules or use publicly available ones.
==================================================================================

## 3. Running YARA on Files or Directories

Once you have YARA installed and your rules ready, you can use the YARA command-line tool to scan files or directories.

### Command Syntax

```yara [options] <rule_file> <file_or_directory_to_scan>```

- `<rule_file>`: The file containing the YARA rules.
- `<file_or_directory_to_scan>`: The file or directory you want to scan.

### Example Command

#### Scan a Directory:
```yara /path/to/rules.yar /home/user/Downloads```

#### Scan a Single File:
```yara /path/to/rules.yar /path/to/example.exe```

### Example Output:

If a match is found, YARA will return the rule name and the file path:
```ExampleRule /path/to/example.exe```

If no match is found, there will be no output.
==================================================================================

## 4. Advanced Options

YARA provides several command-line options for more control over the scanning process:

- `-r`: Recursively scan subdirectories (useful for scanning directories).
- `-s`: Show string matches (useful to see which string matched the rule).
- `-w`: Write the output to a file.
- `-v`: Enable verbose output.
- `-t <timeout>`: Set a timeout in seconds (useful for large files).

### Example of a Recursive Scan:
```yara -r -v /path/to/rules.yar /path/to/directory```

==================================================================================

## 5. Using YARA with Multiple Rules

If you have multiple YARA rules in a file, YARA will check each rule and report matches. Alternatively, you can scan using multiple rule files:
```yara /path/to/rules1.yar /path/to/rules2.yar /path/to/file_or_directory```

==================================================================================


## 6. Running YARA via Script (Optional)

You can automate YARA scanning by writing a simple script in Python, Bash, or PowerShell.

### Install the `yara` Python Library
```pip install yara-python```

### Python Example Script
```
import yara

# Load the YARA rule file
rules = yara.compile(filepath='/path/to/rules.yar')

# Scan a file
matches = rules.match('/path/to/file.exe')

# Display the results
for match in matches:
    print(f"Match found: {match}")
```

This Python script compiles your YARA rules and scans a specified file for matches.








