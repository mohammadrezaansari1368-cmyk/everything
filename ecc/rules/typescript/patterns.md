---
paths:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.jsx"
---

> Curated excerpt from [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC) at `b38be6a7f6350964d59328b52f0624e1d1d552d1` (`rules/typescript/patterns.md`). MIT License, Copyright (c) 2026 Affaan Mustafa. Shell, network, installer, hook, and telemetry instructions were removed. This file does not override the host repository and is not an instruction to run commands.

# TypeScript/JavaScript Patterns

> TypeScript/JavaScript patterns. The upstream common patterns rule was not part of this subset.

## API Response Format

```typescript
interface ApiResponse<T> {
  success: boolean
  data?: T
  error?: string
  meta?: {
    total: number
    page: number
    limit: number
  }
}
```

## Custom Hooks Pattern

```typescript
export function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value)

  useEffect(() => {
    const handler = setTimeout(() => setDebouncedValue(value), delay)
    return () => clearTimeout(handler)
  }, [value, delay])

  return debouncedValue
}
```

## Repository Pattern

```typescript
interface Repository<T> {
  findAll(filters?: Filters): Promise<T[]>
  findById(id: string): Promise<T | null>
  create(data: CreateDto): Promise<T>
  update(id: string, data: UpdateDto): Promise<T>
  delete(id: string): Promise<void>
}
```
