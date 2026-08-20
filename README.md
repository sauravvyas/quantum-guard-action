# 🛡️ QuantumGuard PQC Scanner

**Privacy-first Post-Quantum Cryptography vulnerability scanner and auto-remediator.**

QuantumGuard integrates directly into your CI/CD pipeline to automatically scan your code for legacy cryptography (like RSA and ECC) and helps you seamlessly migrate to quantum-resistant algorithms (Post-Quantum Cryptography).

## 🚀 Features
* **Zero Intellectual Property Leakage:** Scans are performed 100% locally on your runner using Abstract Syntax Tree (AST) parsing. Your source code never leaves your environment.
* **Instant Detection:** Immediately flags vulnerable legacy RSA and ECC implementations.
* **Auto-Remediation:** Automatically suggests drop-in replacements for vulnerable algorithms.
* **Cross-Language:** Deep inspection of cryptography implementations.

## ⚙️ Usage

To use this action, you must generate a License Key from your QuantumGuard Dashboard.

1. Sign up and grab your License Key from [QuantumGuard](https://quantum-guard-cli-backend.vercel.app/).
2. Add your key to your repository's GitHub Secrets as `QUANTUMGUARD_LICENSE_KEY`.
3. Add the following step to your `.github/workflows` file:

```yaml
name: PQC Security Scan

on: [push, pull_request]

jobs:
  quantumguard-scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Run QuantumGuard Scanner
        uses: sauravvyas/quantum-guard-action@v1.0.0
        with:
          license_key: ${{ secrets.QUANTUMGUARD_LICENSE_KEY }}
          target_dir: '.' # Optional: specify a specific directory to scan
