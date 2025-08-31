# 💾 FAT32 File System Shell
<img width="300" height="300" alt="FAT32" src="https://github.com/user-attachments/assets/d484781c-e462-41c3-9397-2a7f5e48419e" />

A user-space shell application implemented in C that interprets a FAT32 file system image.
The project demonstrates file system navigation, file access, and manipulation while ensuring robustness and preserving the integrity of the FAT32 image.

# 📖 About the Project

This project implements a custom shell (mfs) to interact with FAT32 file system images.
It allows users to open, browse, read, write, and manage files and directories within a FAT32 image without mounting it or using kernel-level utilities.

## Key skills demonstrated:
- ⚙️ Systems-level programming in C

- 📂 Understanding FAT32 structures (BPB fields, clusters, directory entries)

- 📑 Implementing file operations (open, close, ls, cd, etc.)

- 🖥️ Shell-based interface with command parsing and error handling

# 🚀 Features

- 🖱️ Interactive Shell Prompt → mfs>

- 📂 File & Directory Commands:

   - open <filename> → open a FAT32 image

   - close → close the current image

   - save [new filename] → save image copy

   - stat <filename> → show file attributes + cluster info

   - cd <directory> → change working directory (supports relative + absolute paths)

   - ls → list directory contents (. and .. supported)

 
- 📜 File Access Commands:

   - get <filename> [new filename] → extract file from FAT32 to host

   - put <filename> [new filename] → add file from host into FAT32 image

   - read <filename> <pos> <bytes> [ascii|dec] → read file data in multiple formats

   - del <filename> → delete file

   - undel <filename> → restore deleted file

 
- ℹ️ Info Command:
   
   - Prints FAT32 BPB fields in hex and decimal:

   - BPB_BytesPerSec, BPB_SecPerClus, BPB_NumFATS, BPB_FATSz32, BPB_RootClus, etc.
 
❌ Error Handling:

Prints one consistent error message for invalid operations:

    char error_message[30] = "An error has occurred\n";
    write(STDERR_FILENO, error_message, strlen(error_message));

# 🛠️ Tech Stack

- Language: C

- Environment: GitHub Codespaces (Linux)

- Build System: GNU Make

- Debugging Tools: GDB

- File System: FAT32

# ▶️ Building and Running

## 🔨 Build
make

## ▶️ Run the Shell
./mfs
mfs> open fat32.img
mfs> info
mfs> ls
mfs> cd /DIRECTORY
mfs> get file.txt
mfs> quit

# 📊 Example Usage
   
mfs> open fat32.img
mfs> info
BPB_BytesPerSec: 512 (0x200)
BPB_SecPerClus: 8 (0x08)
BPB_NumFATS: 2 (0x02)
BPB_FATSz32: 1234 (0x04D2)
BPB_RootClus: 2 (0x02)

mfs> ls
.   ..   FILE1.TXT   FILE2.DAT

mfs> stat FILE1.TXT
Size: 1024 bytes
Attributes: ARCHIVE
Cluster Start: 5

mfs> read FILE1.TXT 0 16 -ascii
Hello FAT32 Shell


🎯 Learning Outcomes

Through this project, I gained hands-on experience in:

- Parsing and interpreting FAT32 metadata and directory entries

- Implementing a command-line shell with custom commands

- Managing file extraction and insertion into FAT32 images

- Handling errors and edge cases gracefully

- Debugging complex pointer and memory management issues in C

# 🚀 Future Enhancements

- 🔀 Add support for long file names (LFN)

- 🧵 Add multi-threading for parallel file operations

- 🔑 Add user authentication layer for controlled access

- 📊 Add reporting commands (disk usage, fragmentation stats)


# ✨ 
This project highlights systems programming, file system knowledge, and C expertise — valuable for OS, embedded systems, and low-level software engineering roles.
