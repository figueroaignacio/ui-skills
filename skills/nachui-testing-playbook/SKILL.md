---
name: "nachui-testing-playbook"
description: "Use when writing or running automated tests inside packages/ui or verify regressions in NachUI."
---

# NachUI Testing Playbook

You are writing and executing tests for the NachUI library. All components must be thoroughly tested using Vitest and React Testing Library (RTL).

## Location & Structure
* All tests must live in the same directory as the source file they target, with the `.test.ts` or `.test.tsx` file extension.
* Ensure code coverage targets user interactions, rendering states, variant combinations, and boundary error conditions.

## Execution Guide
Do NOT use `cd` into packages. Run test commands from the root directory using pnpm workspace filters:

```bash
# Run tests in watch mode (interactive)
pnpm --filter @repo/ui test

# Run a full CI-style run (single run)
pnpm --filter @repo/ui test:run

# Generate test coverage reports
pnpm --filter @repo/ui test:coverage

# Launch Vitest's visual UI dashboard
pnpm --filter @repo/ui test:ui
```

### Running specific files
Run targeted test suites or filters using the native `vitest` CLI arguments directly:

```bash
# Run tests for a specific utility
pnpm --filter @repo/ui vitest run src/lib/cn.test.ts

# Run tests matching a specific component and description
pnpm --filter @repo/ui vitest run src/components/button.test.tsx -t "renders loading state"
```

## Best Practices
1. **User Event Simulation**: Prefer `@testing-library/user-event` over `fireEvent` to accurately simulate real browser interactions.
2. **Accessiblity Queries**: Use semantic accessibility queries (e.g. `getByRole('button', { name: /submit/i })`) over generic `querySelector` or test IDs.
3. **Clean-up**: Ensure mock timers, custom event listeners, or module mocks are cleaned up after each test using `beforeEach` or `afterEach`.
4. **Isolated rendering**: Test components in isolation. Do not import live network utilities; mock external dependencies if required.

## Testing Example

```typescript
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import { describe, expect, it, vi } from 'vitest';
import { Button } from './button';

describe('Button Component', () => {
  it('renders correctly with default values', () => {
    render(<Button>Click me</Button>);
    const button = screen.getByRole('button', { name: /click me/i });
    expect(button).toBeInTheDocument();
  });

  it('triggers onClick handler when clicked', async () => {
    const handleClick = vi.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    
    const button = screen.getByRole('button', { name: /click me/i });
    await userEvent.click(button);
    
    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it('does not trigger onClick when disabled', async () => {
    const handleClick = vi.fn();
    render(<Button onClick={handleClick} disabled>Click me</Button>);
    
    const button = screen.getByRole('button', { name: /click me/i });
    await userEvent.click(button);
    
    expect(handleClick).not.toHaveBeenCalled();
  });
});
```
