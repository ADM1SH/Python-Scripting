# Modrinth Modpack Automated Installer (Python)

[![Language: Python](https://img.shields.io/badge/Language-Python_3.8+-3776AB.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Tool: Modrinth API](https://img.shields.io/badge/API-Modrinth_v2-00AF5C.svg)](https://docs.modrinth.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A command-line Python automation tool that unpacks, verifies, and installs Modrinth `.mrpack` server and client modpacks automatically.

## Description
`mrpack-install.py` is an administrative automation script designed for Minecraft server and client management. Modrinth packages modpacks in the `.mrpack` format: a ZIP archive containing a standardized `modrinth.index.json` manifest and configuration overrides. This tool automates downloading hundreds of mod files concurrently, verifying SHA-512 hashes, extracting overrides, and preparing ready-to-launch server instances.

### Key Capabilities
* **Index Manifest Parsing**: Reads `modrinth.index.json` to extract project IDs, file hashes, download URLs, and environment requirements (client vs server).
* **Cryptographic Integrity Verification**: Automatically hashes downloaded files using SHA-1 and SHA-512 to ensure zero corruption.
* **Override Extraction**: Recursively merges configuration overrides (`/overrides`) into the destination directory.
* **Server/Client Filtering**: Discards client-only mods (like GUI enhancements) when deploying dedicated servers to conserve memory.

## Repository Contents
```text
Python-Scripting/
├── mrpack-install.py   # Standalone CLI modpack installer script
└── README.md           # Documentation and CLI reference
```

## Requirements
* Python: version 3.8 or higher
* Standard library modules: `urllib`, `hashlib`, `json`, `zipfile`, `argparse` (zero external dependencies required)

## Installation
Clone the repository:
```bash
git clone https://github.com/ADM1SH/Python-Scripting.git
cd Python-Scripting
```

Make the script executable:
```bash
chmod +x mrpack-install.py
```

## Usage
Basic usage:
```bash
python3 mrpack-install.py path/to/modpack.mrpack --output /path/to/server
```

CLI options:
```text
usage: mrpack-install.py [-h] [--output DIR] [--server-only] [--threads NUM] mrpack_file

positional arguments:
  mrpack_file       Path to the local .mrpack file or remote download URL

options:
  -h, --help        Show this help message and exit
  --output DIR      Destination installation directory (default: current directory)
  --server-only     Skip client-side mods when deploying a dedicated server
  --threads NUM     Concurrent download worker threads (default: 8)
```

## Support
Submit issues or enhancement requests:
https://github.com/ADM1SH/Python-Scripting/issues

## Roadmap
* [x] Implement `.mrpack` archive decompression.
* [x] Add SHA-512 cryptographic verification.
* [x] Implement override directory merging.
* [ ] Add direct Modrinth slug URL downloading.
* [ ] Add Fabric loader auto-download flag.

## Contributing
1. Fork the repository.
2. Create a branch: `git checkout -b feature/async-downloads`.
3. Test thoroughly with official Modrinth modpacks.
4. Open a Pull Request.

## Authors and Acknowledgment
* **Adam Anwar** (ADM1SH) - Script developer.
* **Modrinth Team** - Standard `.mrpack` specification.

## License
MIT License. See `LICENSE` for details.

## Project Status
Active utility. Maintained for dedicated server administrators and players.
