# Vite - Unit & Component Testing

Vitest is a modern testing framework designed specifically for Vite projects.

In Vite projects, we use Vitest as the test runner. 
For React, we use React Testing Library, 
for Vue, we use Vue Test Utils to test components.

## Uses 

- Unit testing: Testing individual individual functions, components, logic.
- Component testing: Testing React or Vue components in isolation, checking rendering, interactions, state changes.

## Setup

1. Install Vitest and testing libraries:

```bash
npm install --save-dev vitest @testing-library/react @testing-library/vue
```

2. Configure Vitest in `vite.config.js`:

```js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
  plugins: [react(), vue()],
  test: {
    globals: true,
    environment: 'jsdom',
  },
});
```
3. Create test files with `.test.js` or `.spec.js` extension.

## Running Tests
Run tests using the command:

```bash 
npm run test
```

This will execute all test files and display results in the console.
