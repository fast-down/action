# Setup Fast Down Action

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-setup--fast--down-blue.svg?logo=github)](https://github.com/marketplace/actions/setup-fast-down)
[![GitHub last commit](https://img.shields.io/github/last-commit/fast-down/action/main)](https://github.com/fast-down/action/commits/main)
[![Test](https://github.com/fast-down/action/workflows/Test/badge.svg)](https://github.com/fast-down/action/actions)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/fast-down/action/blob/main/LICENSE)

This GitHub Action sets up **[fast-down](https://github.com/fast-down/cli)** — the fastest concurrent downloader — for your CI/CD workflows.

It automatically downloads the correct binary for the runner's OS/Arch, renames it to `fd`, and adds it to the system `PATH`.

## Features

1. **⚡️ Zero Configuration**
   Automatically detects **Linux**, **Windows**, and **macOS** environments and downloads the appropriate binary.
2. **🔄 Cross-Architecture Support**
   Supports **x64**, **ARM64**, and **32-bit** (Linux/Windows) architectures seamlessly.
3. **🛠️ Ready to Use**
   Installs the binary as `fd` (or `fd.exe`) and adds it to the `PATH`, so you can immediately run `fd download ...`.
4. **🎯 Version Control**
   Supports installing specific versions or defaulting to the `latest` stable release.

## Supported Platforms

| Arch   | Windows | Linux | Mac OS |
| :--- | :---: | :---: | :---: |
| **64 bit** | ✅ | ✅ | ✅ |
| **Arm64** | ✅ | ✅ | ✅ |
| **32 bit** | ✅ | ✅ | ❌ |

## Usage

### Basic Usage (Latest Version)

```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v4

  - name: Setup fast-down
    uses: fast-down/action@v1

  - name: Download a file
    run: fd "https://example.com/large-file.zip" -o file.zip
```

### Pin a Specific Version

```yaml
steps:
  - name: Setup fast-down (Specific Version)
    uses: fast-down/action@v1
    with:
      version: '2.6.0' # Specify the version you need

  - name: Check version
    run: fd -h
```

## Inputs

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `version` | The version of fast-down to install (e.g., `latest`, `2.6.0`). | No | `latest` |
