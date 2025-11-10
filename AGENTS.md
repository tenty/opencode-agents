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

## Opencode Agents

### Plan and Resume Agent
- **Type**: OpenCode Subagent
- **Configuration**: `.opencode/agent/plan-resume.md` and `opencode.json`
- **Purpose**: Reviews AGENTS.md, README.md, and other documentation before starting project work
- **Usage**: Invoke with `@plan-resume` in OpenCode conversations
- **Capabilities**: Read-only access to documentation files

### Close Out Agent
- **Type**: OpenCode Subagent
- **Configuration**: `.opencode/agent/close-out.md` and `opencode.json`
- **Purpose**: Updates documentation files with current project information and creates necessary docs
- **Usage**: Invoke with `@close-out` at the end of coding sessions
- **Capabilities**: Read and write access to documentation files

### Cybersecurity Critic Agent
- **Type**: OpenCode Subagent
- **Configuration**: `.opencode/agent/cybersecurity-critic.md` and `opencode.json`
- **Purpose**: Vets code for security vulnerabilities, automatically fixes critical/high issues, prompts for medium/low fixes
- **Usage**: Invoke with `@cybersecurity-critic` during development
- **Capabilities**: Read and write access to source code for security fixes