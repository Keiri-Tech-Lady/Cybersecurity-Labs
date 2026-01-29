# Cybersecurity-Labs
A collection of hands-on technical labs, network security configurations, and troubleshooting logs documenting my journey as a Cybersecurity Analyst Fellow.
---

## 🛠 Troubleshooting Log: macOS Environment Setup

**Issue:** `zsh: command not found: brew` after a successful Homebrew installation.

**Root Cause Analysis:** On Apple Silicon Macs, the binary path `/opt/homebrew/bin` is not automatically added to the system `$PATH`. Without this mapping, the shell cannot locate the executable.

**Remediation Steps:**
1. Appended the Homebrew initialization script to the local shell profile (`.zprofile`).
2. Executed: `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile`
3. Refreshed the environment with: `eval "$(/opt/homebrew/bin/brew shellenv)"`

**Outcome:** Environment successfully configured. Verified by successfully running `brew install git`.
