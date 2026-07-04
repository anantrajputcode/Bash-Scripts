# filesorg
A Bash script that automates organizing files in a directory into subfolders based on their file extension.

## Overview
This script was built to remove the manual effort of sorting cluttered directories — like Downloads folders — into tidy, extension-based subfolders. It runs a simple scan-and-move cycle each time it's executed, making it suitable for periodic use via cron or manual runs.

## What It Does
1. Verifies the target directory exists before doing anything
2. Scans the directory for regular files (subdirectories are skipped)
3. Determines each file's extension
4. Creates a subfolder for that extension if one doesn't already exist
5. Moves the file into its matching extension subfolder

## Usage
```bash
filesorg <directory>
```
If the script's directory has been added to your `$PATH`, it can be run from anywhere. Otherwise, run it directly:
```bash
./filesorg <directory>
```

## Configuration
This script takes its target directory as a command-line argument rather than a hardcoded variable:

| Argument | Description |
|---|---|
| `$1` | Path to the directory whose files should be sorted |

## Output
Files are reorganized in place, inside the target directory:
```
<directory>/
├── jpg/
│   └── photo.jpg
├── pdf/
│   └── invoice.pdf
└── txt/
    └── notes.txt
```

## Requirements
- Bash
- Standard Unix utilities: `mv`, `mkdir`

## Automating with Cron
To run this automatically, for example every day at midnight, add the following to your crontab:
```bash
crontab -e
```
```
0 0 * * * /path/to/filesorg /path/to/target-directory
```

## Notes
- Only regular files are moved; subdirectories in the target folder are left untouched.
- Files without a file extension will currently be grouped under a folder named after the full filename — a known limitation worth improving if your directory has extensionless files.
- Running the script more than once on an already-sorted directory is safe; it simply re-checks each file's location.

## Example
```bash
$ filesorg ~/Downloads
```
```
~/Downloads/jpg/photo.jpg
~/Downloads/pdf/invoice.pdf
~/Downloads/txt/notes.txt
```

## License
This script is part of the [bash-scripts](../) collection and is licensed under the MIT License.
