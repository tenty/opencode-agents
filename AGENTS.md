# AGENTS.md

## Build/Lint/Test Commands
- **Build**: `npm run build` or `yarn build`
- **Lint**: `npm run lint` or `yarn lint`
- **Test All**: `npm test` or `yarn test`
- **Test Single**: `npm test -- --testNamePattern="test name"` or `yarn test --testNamePattern="test name"`

## Code Style Guidelines

### Imports
- Use ES6 imports with named imports when possible
- Group imports: external libraries first, then internal modules
- Sort imports alphabetically within groups

### Formatting
- Use consistent indentation (2 spaces preferred)
- Max line length: 100 characters
- Use semicolons

### Types
- Use TypeScript for type safety
- Prefer interfaces over types for object shapes
- Use union types for related variants

### Naming Conventions
- Variables/functions: camelCase
- Classes/Types: PascalCase
- Constants: UPPER_SNAKE_CASE
- Files: kebab-case.ts

### Error Handling
- Use try/catch for async operations
- Throw descriptive Error objects
- Handle errors at appropriate levels

### General
- Write self-documenting code
- Use meaningful variable names
- Keep functions small and focused
- Add JSDoc for complex functions

## Available Agents

This project includes the following specialized agents:

### 🔍 Plan and Resume Agent
- **Usage**: `@plan-resume`
- **Purpose**: Reviews project documentation before starting work
- **Capabilities**: Read-only access to documentation files

### 📝 Close Out Agent
- **Usage**: `@close-out`
- **Purpose**: Updates documentation at the end of coding sessions
- **Capabilities**: Read and write access to documentation files

### 🛡️ Security Critic Agent
- **Usage**: `@security-critic`
- **Purpose**: Analyzes code for security vulnerabilities with plain English explanations

#### What it does:
- Identifies common security vulnerabilities (SQL injection, XSS, hardcoded secrets, etc.)
- Provides plain English explanations of why issues are dangerous
- Offers actionable fix recommendations
- Categorizes issues by severity (HIGH/MEDIUM/LOW)

#### When to use:
- Before committing code changes
- During code reviews
- When implementing authentication or authorization
- When handling user input or file operations
- Before deploying to production

#### Example usage:
```
@security-critic review the authentication code in auth.py
```

```
@security-critic check for security issues in the user registration flow
```

#### Security issues detected:
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

1. Use `@plan-resume` to review project documentation
2. Use `@security-critic` to invoke the security analyst
3. Use `@close-out` to update documentation at session end
4. Switch between agents using the Tab key
5. Use the Plan agent for safe analysis without making changes

Remember: Security is everyone's responsibility. Use the Security Critic Agent regularly to catch vulnerabilities early!
