---
layout: default
---

# Taking it Further

Orval has an extensive hooks system, allowing you to automatically run scripts at various stages in the code generation process.

For example, after all the API code has been generated, we can generated Pinia Colada wrappers around this.

Or, we can generate Zod Schemas from our OpenAPI spec

```ts [orval.config.ts] {all|5-7|27-37} {maxHeight: '300px'}
import { defineConfig } from 'orval';

export default defineConfig({
  server: {
    hooks: {
      afterAllFilesWrite: ['pnpm exec jiti ./orval/generate-colada-wrappers.ts'],
    },
    output: {
      mode: 'tags-split',
      target: 'src/api/endpoints',
      schemas: 'src/api/models',
      baseUrl: 'http://localhost:3000',
      client: 'fetch',
      mock: true,
    },
    input: {
      target: '../server/openapi.json',
    },
  },
  serverZod: {
    input: {
      target: '../server/openapi.json',
    },
    output: {
      mode: 'tags-split',
      client: 'zod',
      target: 'src/api/endpoints',
      fileExtension: '.zod.ts',
    },
  },
});

```
