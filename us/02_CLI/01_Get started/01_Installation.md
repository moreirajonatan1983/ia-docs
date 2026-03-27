# Installation — Kiro CLI

> **Source:** [kiro.dev/docs/cli/installation/](https://kiro.dev/docs/cli/installation/)

---

## macOS

You can natively install Kiro CLI for macOS at the command line:

```bash
curl -fsSL https://cli.kiro.dev/install | bash
```

Kiro will direct you to open your web browser, where you will follow the steps under [Authentication](https://kiro.dev/docs/cli/authentication).

---

## Linux — AppImage

You can install Kiro CLI for Linux using the AppImage format, which is portable and works on most Linux distributions without requiring installation.

1. Download Kiro CLI for Linux AppImage:
   ```
   https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.appimage
   ```

2. Make the AppImage executable:
   ```bash
   chmod +x kiro-cli.appimage
   ```

3. Run the AppImage:
   ```bash
   ./kiro-cli.appimage
   ```

4. Kiro will direct you to open your web browser to follow the [Authentication](https://kiro.dev/docs/cli/authentication) steps.

---

## Linux — With a Zip File

### Install and Update Requirements

- You must be able to extract or "unzip" the downloaded package.
- Kiro CLI requires **glibc 2.34 or newer** (included by default in most major Linux distributions released since 2021).
- For older distributions with glibc < 2.34, use the special **musl-based version** (indicated by `-musl.zip` in the filename).
- Supported on **64-bit x86_64** and **ARM aarch64** versions of: Fedora, Ubuntu, Amazon Linux 2023.

### Checking Your glibc Version

```bash
ldd --version
```

- If **2.34 or newer** → use the standard version.
- If **older** → use the musl version.

### Download the Installation File

**Standard version (glibc 2.34+):**

Linux x86-64:
```bash
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux.zip' \
  -o 'kirocli.zip'
```

Linux ARM (aarch64):
```bash
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux.zip' \
  -o 'kirocli.zip'
```

**Musl version (for glibc < 2.34):**

Linux x86-64 with musl:
```bash
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux-musl.zip' \
  -o 'kirocli.zip'
```

Linux ARM (aarch64) with musl:
```bash
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux-musl.zip' \
  -o 'kirocli.zip'
```

### Install Kiro CLI

1. Unzip the installer:
   ```bash
   unzip kirocli.zip
   ```

2. Run the install program:
   ```bash
   ./kirocli/install.sh
   ```

   By default, files are installed to `~/.local/bin`.

---

## Linux — Ubuntu (.deb package)

1. Download Kiro CLI for Ubuntu:
   ```bash
   wget https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.deb
   ```

2. Install the package:
   ```bash
   sudo dpkg -i kiro-cli.deb
   sudo apt-get install -f
   ```

3. Launch Kiro CLI:
   ```bash
   kiro-cli
   ```

4. Kiro will direct you to open your web browser to follow the [Authentication](https://kiro.dev/docs/cli/authentication) steps.

---

## Proxy Configuration

Kiro CLI (v1.8.0 and later) supports proxy servers commonly used in enterprise environments. The CLI automatically respects standard proxy environment variables.

### Setting Proxy Environment Variables

```bash
# HTTP proxy for non-SSL traffic
export HTTP_PROXY=http://proxy.company.com:8080

# HTTPS proxy for SSL traffic
export HTTPS_PROXY=http://proxy.company.com:8080

# Bypass proxy for specific domains
export NO_PROXY=localhost,127.0.0.1,.company.com
```

### Proxy with Authentication

```bash
export HTTP_PROXY=http://username:password@proxy.company.com:8080
export HTTPS_PROXY=http://username:password@proxy.company.com:8080
```

### Troubleshooting Proxy Issues

- Verify proxy server accessibility and credentials
- Ensure your corporate firewall allows connections to AWS endpoints
- Contact your IT administrator if SSL certificate validation fails
- Check that the proxy server supports the required protocols

---

## Uninstalling Kiro CLI

**macOS:**
```bash
kiro-cli uninstall
```

**Ubuntu:**
```bash
sudo apt-get remove kiro-cli
sudo apt-get purge kiro-cli   # Remove remaining config files
```

---

## Debugging Kiro CLI

If you're having a problem with Kiro CLI, run `kiro-cli doctor` to identify and fix common issues:

```bash
kiro-cli doctor
```

---

## Next Steps

- [Authentication →](https://kiro.dev/docs/cli/authentication/)
- [Models →](https://kiro.dev/docs/cli/models/)