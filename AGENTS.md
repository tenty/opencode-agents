# Available Agents

This project includes the following specialized agents:

## 🔍 Security Critic Agent

**Usage**: `@security-critic`

A specialized cybersecurity agent that analyzes code for security vulnerabilities and provides clear explanations in plain English.

### What it does:
- Identifies common security vulnerabilities (SQL injection, XSS, hardcoded secrets, etc.)
- Provides plain English explanations of why issues are dangerous
- Offers actionable fix recommendations
- Categorizes issues by severity (HIGH/MEDIUM/LOW)

### When to use:
- Before committing code changes
- During code reviews
- When implementing authentication or authorization
- When handling user input or file operations
- Before deploying to production

### Example usage:
```
@security-critic review the authentication code in auth.py
```

```
@security-critic check for security issues in the user registration flow
```

### Security issues detected:
- SQL Injection
- Hardcoded Secrets
- Path Traversal
- Cross-Site Scripting (XSS)
- Weak Cryptography
- Dynamic Code Execution
- Command Injection
- Insecure Random Generation
- And more...

## Built-in Agents

### Build Agent
Default agent for development work with full tool access.

### Plan Agent  
Analysis and planning agent with restricted permissions for safe code review.

### General Agent
General-purpose agent for research and multi-step tasks.

---

## Getting Started

1. Use `@security-critic` to invoke the security analyst
2. Switch between agents using the Tab key
3. Use the Plan agent for safe code analysis without making changes

Remember: Security is everyone's responsibility. Use the Security Critic Agent regularly to catch vulnerabilities early!