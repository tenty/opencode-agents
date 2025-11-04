# Example: Using the Security Critic Agent in OpenCode

This file demonstrates how you would use the @security-critic agent within OpenCode.

## Example Usage

### Basic Security Review
```
@security-critic review this file for security vulnerabilities
```

### Specific Security Concern
```
@security-critic check the login function for authentication issues
```

### Framework-Specific Analysis
```
@security-critic analyze this Express.js route for injection vulnerabilities
```

### Before Deployment
```
@security-critic perform a security audit of the entire codebase
```

## What to Expect

When you invoke @security-critic, it will:

1. **Scan the code** for known vulnerability patterns
2. **Identify issues** with specific line numbers
3. **Explain risks** in plain English
4. **Provide solutions** with code examples
5. **Categorize by severity** (HIGH/MEDIUM/LOW)

## Example Response

```
🚨 HIGH SEVERITY: SQL Injection Risk
Location: Line 23 in database.py
Code: query = f"SELECT * FROM users WHERE email = '{email}'"

Why it's dangerous: An attacker could input malicious SQL code that bypasses authentication or steals user data from your database.

How to fix: Use parameterized queries:
```python
query = "SELECT * FROM users WHERE email = ?"
cursor.execute(query, (email,))
```

This prevents attackers from injecting SQL commands into your queries.
```

## Integration Workflow

1. **Development**: Write your code
2. **Review**: Use @security-critic to check for issues
3. **Fix**: Apply the recommended changes
4. **Verify**: Run @security-critic again to confirm fixes
5. **Deploy**: Ship with confidence

## Best Practices

- Use @security-critic early and often in development
- Run it before every commit or pull request
- Pay special attention to HIGH severity issues
- Use the Plan agent for safe analysis without making changes
- Combine with regular code reviews for comprehensive coverage

The Security Critic Agent helps make cybersecurity accessible to developers at all skill levels!