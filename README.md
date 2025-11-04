# OpenCode Security Critic Agent

🛡️ A specialized cybersecurity agent for OpenCode that analyzes code for security vulnerabilities and provides clear explanations in plain English.

[![OpenCode Agents](https://img.shields.io/badge/OpenCode-Agent-blue)](https://opencode.ai)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

The Security Critic Agent helps developers identify and fix security vulnerabilities in their code. It provides:

- 🔍 **Comprehensive Security Analysis** - Detects common vulnerabilities like SQL injection, XSS, hardcoded secrets, and more
- 📚 **Plain English Explanations** - Security issues explained without technical jargon
- 🎯 **Actionable Recommendations** - Specific fix suggestions with code examples
- 🚨 **Severity Classification** - Issues categorized as HIGH, MEDIUM, or LOW priority
- 🔒 **Safe by Default** - Read-only permissions prevent accidental code changes

## Quick Start

This guide shows you how to add the Cybersecurity Critic Agent to your OpenCode installation.

## Quick Start

### Option 1: Project-Specific Installation (Recommended)

1. **Copy the agent file to your project:**
   ```bash
   mkdir -p .opencode/agent
   cp security-critic.md .opencode/agent/
   ```

2. **Add to your project's AGENTS.md:**
   ```bash
   cp AGENTS.md ./
   ```

3. **Start OpenCode in your project:**
   ```bash
   opencode
   ```

4. **Use the agent:**
   ```
   @security-critic review my code for security issues
   ```

### Option 2: Global Installation

1. **Create global agent directory:**
   ```bash
   mkdir -p ~/.config/opencode/agent
   ```

2. **Copy the agent globally:**
   ```bash
   cp security-critic.md ~/.config/opencode/agent/
   ```

3. **Available in all OpenCode sessions**

### Option 3: JSON Configuration

1. **Add to your opencode.json:**
   ```bash
   cp opencode-security.json ./opencode.json
   ```

2. **Or merge with existing configuration**

## Usage Examples

### Basic Security Review
```
@security-critic analyze the authentication system
```

### Specific File Analysis
```
@security-critic check login.py for security vulnerabilities
```

### Framework-Specific
```
@security-critic review this Express.js API for injection attacks
```

### Before Deployment
```
@security-critic perform security audit of entire codebase
```

## What the Agent Detects

### 🚨 HIGH SEVERITY
- SQL Injection
- Hardcoded Secrets (API keys, passwords)
- Path Traversal
- Dynamic Code Execution
- Command Injection

### ⚠️ MEDIUM SEVERITY
- Cross-Site Scripting (XSS)
- Weak Cryptography (MD5, SHA1)
- Insecure Random Generation
- Insecure Deserialization

### ℹ️ LOW SEVERITY
- Information Disclosure
- Insufficient Logging
- Weak Password Policies

## Integration with Development Workflow

### Pre-commit Hook
```bash
#!/bin/sh
# .git/hooks/pre-commit
opencode agent run security-critic --files=$(git diff --cached --name-only)
if [ $? -ne 0 ]; then
    echo "Security issues found! Please review before committing."
    exit 1
fi
```

### CI/CD Integration
```yaml
# .github/workflows/security.yml
name: Security Review
on: [push, pull_request]
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run Security Critic
      run: |
        opencode agent run security-critic --format json > security-report.json
    - name: Upload Report
      uses: actions/upload-artifact@v2
      with:
        name: security-report
        path: security-report.json
```

## Configuration Options

### Model Selection
You can specify different models in the agent configuration:

```yaml
model: anthropic/claude-haiku-4-20250514  # Faster, less expensive
model: anthropic/claude-sonnet-4-20250514  # Balanced (recommended)
model: anthropic/claude-opus-4-20250514   # Most capable
```

### Temperature Settings
- `0.0-0.2`: Very focused analysis (recommended for security)
- `0.3-0.5`: Balanced responses
- `0.6-1.0`: More creative exploration

### Tool Permissions
The agent is configured with read-only permissions by default:
- ✅ Read files
- ✅ Search code
- ✅ Fetch documentation
- ❌ Edit files
- ❌ Run commands
- ❌ Write files

## Best Practices

1. **Use Early and Often**: Run security reviews during development, not just before deployment
2. **Combine with Human Review**: Use the agent as a supplement to, not replacement for, code reviews
3. **Focus on HIGH Issues**: Prioritize fixing HIGH severity issues first
4. **Learn from Recommendations**: Use the explanations to improve your security knowledge
5. **Update Regularly**: Keep the agent updated for the latest security patterns

## Troubleshooting

### Agent Not Found
```bash
# Check if agent file exists
ls .opencode/agent/security-critic.md

# Restart OpenCode
# Exit and restart opencode
```

### Permission Issues
```bash
# Check file permissions
ls -la .opencode/agent/security-critic.md

# Fix permissions if needed
chmod 644 .opencode/agent/security-critic.md
```

### Model Not Available
```bash
# Check available models
opencode models

# Update agent configuration with available model
```

## Contributing

To improve the Security Critic Agent:

1. **Add New Patterns**: Update the agent prompt with new vulnerability patterns
2. **Improve Explanations**: Make security explanations clearer and more accessible
3. **Framework Support**: Add framework-specific security patterns
4. **False Positive Reduction**: Fine-tune patterns to reduce false positives

## Support

- **Documentation**: See SECURITY_USAGE.md for detailed examples
- **Issues**: Report bugs or request features on the OpenCode GitHub repository
- **Community**: Join the OpenCode Discord for community support

---

## 🚀 What's Included

This repository contains:

- **Security Critic Agent** (`security-critic.md`) - Main agent configuration
- **Installation Guide** - Step-by-step setup instructions
- **Usage Examples** - Real-world examples and best practices
- **JSON Configuration** - Alternative configuration format
- **Documentation** - Comprehensive guides and references

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Add New Security Patterns** - Update the agent with new vulnerability detection
2. **Improve Explanations** - Make security advice clearer and more accessible
3. **Framework Support** - Add patterns for specific frameworks
4. **Bug Reports** - Report issues or false positives
5. **Documentation** - Improve guides and examples

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [OpenCode Documentation](https://opencode.ai/docs)
- [OpenCode GitHub](https://github.com/sst/opencode)
- [Security Best Practices](https://owasp.org/)

---

🔍 **Happy secure coding!** Use the Security Critic Agent to catch vulnerabilities early and build more secure applications.