# SWYH-RS for ARM64 Linux
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A "Stream-What-You-Hear" implementation for ARM64 Linux Ubuntu, based on the original [SWYH-RS](https://github.com/dheijl/swyh-rs) by dheijl.

## 🚀 Quick Start

### Pre-compiled Binaries
1. Extract the archive
2. Run either:
   ```bash
   ./rs-cli
   # or
   ./swyh-rs
   ```
3. Test in your browser:
   ```
   http://localhost:5901/stream/swyh.wav
   ```

> ⚠️ **Remember**: Configure your firewall and port forwarding for external access!

## 🔧 Building from Source

### Prerequisites

Install required system dependencies:
```bash
# UI dependencies
sudo apt install -y libx11-dev libxext-dev libxft-dev libxinerama-dev \
                    libxcursor-dev libxrender-dev libxfixes-dev \
                    libpango1.0-dev libgl1-mesa-dev libglu1-mesa-dev

# Audio dependencies
sudo apt install -y libasound2-dev
```

### Install Rust
```bash
RUSTUP_INIT_SKIP_PATH_CHECK=yes curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
# Select option 1 when prompted
```
> 📝 **Note**: Remember to restart your terminal after installing Rust

sudo apt -y install pulseaudio pavucontrol

### Firewall Configuration

Configure UFW rules for DLNA/UPNP and streaming:
```bash
# DLNA/UPNP
sudo ufw allow in from 192.168.0.0/24 to any port 1900 proto udp
sudo ufw allow in from fc00::/7 to any port 1900 proto udp

# UDP Ports
sudo ufw allow in from 192.168.0.0/24 to any port 32000:60000 proto udp
sudo ufw allow in from fc00::/7 to any port 32000:60000 proto udp

# Streaming Port
sudo ufw allow in from 192.168.0.0/24 to any port 5901 proto tcp
sudo ufw allow in from fc00::/7 to any port 5901 proto tcp

# Apply changes
sudo ufw reload
```

### Build Process
Optional commands:

rustup component add rustfmt

1. Clone the repository
2. git clone https://github.com/dheijl/swyh-rs
   
3. Run the build script:
   ```bash

   rustup component add rustfmt

   ./buildall
   ```
4. Find the compiled binary in:
   ```
   swyh-rs-1.12.0/target/release/
   ```

## 🔗 Resources
- Original Project: [dheijl/swyh-rs](https://github.com/dheijl/swyh-rs)
- ARM Port: [jamieduk/SWYH-ARM-64Bit-Linux](https://github.com/jamieduk/SWYH-ARM-64Bit-Linux)

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
