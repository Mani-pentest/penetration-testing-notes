# CH-14: Archiving & Compression

## Overview
Archiving combines multiple files/folders into a single file for easier storage or transfer. Compression reduces file size, and the two are often distributed together using `tar` and `gzip`, or as `.zip` archives.

## Why It Matters
You'll frequently need to package loot or exfiltrated data into a single file for transfer, or extract tools distributed as compressed archives.

## tar Flag Breakdown
| Flag | Meaning |
|------|---------|
| `c` | Create a new archive |
| `x` | Extract an archive |
| `z` | Compress/decompress using `gzip` |
| `v` | Verbose — show which files are processed |
| `f` | Specify the filename immediately after |

## tar / gzip Commands
| Command | Definition |
|---------|------------|
| `tar -cvf archive.tar folder/` | Create an uncompressed archive from a folder |
| `tar -xvf archive.tar` | Extract an uncompressed archive |
| `tar -czvf archive.tar.gz folder/` | Create a compressed archive (tar + gzip) |
| `tar -xzvf archive.tar.gz` | Extract a compressed archive |
| `tar -xzvf backup.tar.gz -C /tmp/` | Extract into a specific directory (`-C`) |
| `gzip file.txt` | Compress a single file → creates `file.txt.gz` (removes original) |
| `gunzip file.txt.gz` | Decompress `file.txt.gz` back to its original format |

## zip / unzip Commands
| Command | Definition |
|---------|------------|
| `zip archive.zip file.txt` | Compress a single file into `archive.zip` |
| `zip archive.zip file1.txt file2.txt` | Compress multiple files into one archive |
| `zip -r archive.zip folder/` | Compress an entire folder recursively (`-r`) |
| `unzip archive.zip` | Extract a `.zip` archive to the current directory |
| `unzip archive.zip -d /tmp/` | Extract to a specific directory (`-d`) |
| `unzip -l archive.zip` | List the contents of a `.zip` archive without extracting |

## Practical Example
| Command | Purpose |
|---------|---------|
| `tar -cvf backup.tar /home/kali/loot` | Archive the loot folder into `backup.tar` |
| `tar -xzvf backup.tar.gz -C /tmp/` | Extract a compressed backup into `/tmp/` |
| `zip -r loot.zip /home/kali/loot` | Zip the loot folder for transfer |
| `unzip loot.zip -d /tmp/extracted` | Extract a downloaded zip into a chosen folder |

## Summary
- `tar` bundles files together; adding `-z` layers in gzip compression.
- `gzip`/`gunzip` handle single-file compression; `tar` handles the more universal archive format.
- `zip`/`unzip` handle the `.zip` format — common when tools or loot are distributed from Windows sources; `-r` zips a whole folder, `-d` unzips into a chosen directory.
