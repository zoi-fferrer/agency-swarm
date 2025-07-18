# ESLint Configuration - Airbnb Setup

This repository includes a comprehensive ESLint configuration based on Airbnb's style guide, with additional support for TypeScript, React, and Prettier integration.

## Files Added

- `.eslintrc.js` - Main ESLint configuration file
- `.eslintignore` - Files and directories to ignore during linting
- `package.json` - Dependencies required for the ESLint setup
- `tsconfig.json` - TypeScript configuration (required by ESLint TypeScript rules)

## Features

### Extends
- **airbnb**: Core Airbnb JavaScript style guide
- **airbnb-typescript**: TypeScript-specific Airbnb rules
- **airbnb/hooks**: React Hooks specific rules
- **@typescript-eslint/recommended**: TypeScript ESLint recommended rules
- **prettier**: Prettier integration to avoid conflicts

### Supported Environments
- Browser environment
- Node.js environment
- ES2021 features
- Jest testing environment

### Key Rules Configured

#### TypeScript
- Unused variables with `_` prefix are ignored
- Flexible function return type requirements
- Warning level for `any` types and unsafe operations

#### React
- No need to import React in JSX files (React 17+)
- Arrow function components preferred
- Prop spreading allowed
- PropTypes not required (using TypeScript instead)

#### Import/Export
- TypeScript file extensions resolved automatically
- Flexible default export rules

#### Code Quality
- Console statements generate warnings
- Debugger statements are errors
- Prefer const, template literals, and modern ES features

### File-Specific Overrides

#### JavaScript Files (`*.js`, `*.jsx`)
- Relaxed TypeScript rules for pure JavaScript files

#### Test Files
- Relaxed rules for test and spec files
- Allow `any` types in tests
- Allow dev dependencies

#### Configuration Files
- Relaxed rules for config files like `webpack.config.js`, `next.config.js`

## Installation

Install the required dependencies:

```bash
npm install
```

## Usage

### Linting Commands

```bash
# Lint all files
npm run lint

# Lint and automatically fix issues
npm run lint:fix

# Lint with zero warnings tolerance (CI/CD)
npm run lint:check
```

### Manual Commands

```bash
# Lint specific files
npx eslint src/components/MyComponent.tsx

# Lint and fix specific files
npx eslint src/components/MyComponent.tsx --fix

# Lint with specific extensions
npx eslint . --ext .js,.jsx,.ts,.tsx
```

## IDE Integration

### VS Code

Install the ESLint extension and add to your VS Code settings:

```json
{
  "eslint.enable": true,
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}
```

### WebStorm/IntelliJ

ESLint integration is built-in. Go to:
`Settings > Languages & Frameworks > JavaScript > Code Quality Tools > ESLint`
Enable ESLint and point to your configuration file.

## Prettier Integration

The configuration includes Prettier integration. The Prettier settings are configured to match the existing `.prettierrc` in the docs folder:

- Semi-colons: enabled
- Quotes: double quotes
- Tab width: 2 spaces
- Print width: 120 characters
- Bracket spacing: enabled
- Arrow parentheses: always
- Trailing comma: none

## Customization

To customize rules, edit `.eslintrc.js`:

```javascript
module.exports = {
  // ... existing configuration
  rules: {
    // Add or override rules here
    'no-console': 'off', // Example: disable console warnings
    'react/jsx-props-no-spreading': 'error', // Example: make prop spreading an error
  },
};
```

## Ignored Files

The `.eslintignore` file excludes:
- Node modules and dependencies
- Build outputs (dist, build, .next)
- Environment files
- IDE-specific files
- Minified files
- Log files
- Python-related files (since this is primarily a Python project)
- Documentation build files

## Notes

- This configuration is designed to work with both pure JavaScript and TypeScript projects
- React dependencies are marked as optional peer dependencies
- The configuration assumes Node.js version 16 or higher
- For projects without React, you can remove React-related plugins and rules
- The TypeScript configuration is optional and can be customized based on your project needs

## Troubleshooting

### Common Issues

1. **"Cannot find module 'typescript'"**: Install TypeScript as a dev dependency
2. **"Cannot read tsconfig.json"**: Ensure the tsconfig.json file exists in the project root
3. **Prettier conflicts**: Make sure `eslint-config-prettier` is the last item in the extends array

### Disabling Rules Temporarily

```javascript
/* eslint-disable no-console */
console.log('This will not trigger a warning');
/* eslint-enable no-console */

// For a single line
console.log('This will not trigger a warning'); // eslint-disable-line no-console
```