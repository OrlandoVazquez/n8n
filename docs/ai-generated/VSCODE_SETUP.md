# ✅ Configuración de VS Code para n8n

## 🔧 Extensiones Recomendadas (INSTALAR AHORA)

### CRÍTICAS (Must-have)
```
1. TypeScript Vue Plugin (Volar)
   ID: Vue.volar
   
2. ESLint
   ID: dbaeumer.vscode-eslint
   
3. Prettier - Code formatter
   ID: esbenp.prettier-vscode
```

### ALTAMENTE RECOMENDADAS
```
4. Biome (linter/formatter oficial)
   ID: biomejs.biome
   
5. Turbo Console Log
   ID: ChakrounSamuel.turbo-console-log
   
6. REST Client
   ID: humao.rest-client
   
7. GitLens — Git supercharged
   ID: eamodio.gitlens
```

### TESTING
```
8. Jest
   ID: firsttris.vscode-jest-runner
   
9. Playwright Test for VSCode
   ID: ms-playwright.playwright
```

### ÚTILES
```
10. Error Lens
    ID: usernamehw.errorlens
    
11. TODO Highlight
    ID: wayou.vscode-todo-highlight
```

## ⚙️ Settings JSON Recomendados

Crea o actualiza `.vscode/settings.json` con esto:

```json
{
  // ==================== GENERAL ====================
  "editor.defaultFormatter": "biomejs.biome",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.biome": "explicit",
    "source.organizeImports": "explicit"
  },
  "editor.rulers": [80, 120],
  "editor.wordWrap": "on",
  
  // ==================== ARCHIVOS ====================
  "files.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/.turbo": true,
    "**/.nuxt": true
  },
  "files.watcherExclude": {
    "**/node_modules/**": true,
    "**/.turbo/**": true,
    "**/dist/**": true
  },
  
  // ==================== TYPESCRIPT ====================
  "typescript.tsdk": "node_modules/typescript/lib",
  "typescript.enablePromptUseWorkspaceTsdk": true,
  "typescript.preferences.importModuleSpecifierFormat": "relative",
  "typescript.preferences.useExplicitTypes": true,
  "[typescript]": {
    "editor.defaultFormatter": "biomejs.biome",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "quickfix.biome.lint.fix": "explicit"
    }
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "biomejs.biome",
    "editor.formatOnSave": true
  },
  
  // ==================== VUE ====================
  "[vue]": {
    "editor.defaultFormatter": "Vue.volar",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll": "explicit"
    }
  },
  
  // ==================== ESLINT ====================
  "eslint.validate": ["typescript", "typescriptreact", "vue", "javascript"],
  "eslint.format.enable": true,
  
  // ==================== TESTING ====================
  "jest.autoRun": "off",
  "jest.runMode": "on-demand",
  "jest.showCoverageOnLoad": false,
  
  // ==================== PRETTIER (si está instalado) ====================
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  
  // ==================== MONOREPO / TURBO ====================
  "search.exclude": {
    "**/node_modules": true,
    "**/.turbo": true,
    "**/dist": true,
    "**/pnpm-lock.yaml": true
  },
  
  // ==================== THEME & APPEARANCE ====================
  "editor.theme": "Default Dark Modern",
  "workbench.iconTheme": "vs-minimal",
  "editor.lineNumbers": "on",
  "editor.minimap.enabled": true,
  "editor.suggest.showStatusBar": true,
  
  // ==================== ERROR LENS ====================
  "errorLens.enableOnDiagnosticRelatedInformation": true
}
```

## ✅ Validación del tsconfig.json

Tu `tsconfig.json` en `packages/testing/playwright/` **está CORRECTO**:

```json
{
  "extends": "../../../tsconfig.json",           // ✅ Hereda config raíz
  "compilerOptions": {
    "sourceMap": false,                          // ✅ Para tests, no necesita
    "declaration": false,                        // ✅ Correcto para tests
    "lib": ["esnext", "dom"],                    // ✅ Playwright necesita dom
    "types": ["@playwright/test", "node"]        // ✅ Tipos de Playwright
  },
  "include": ["**/*.ts"],
  "exclude": ["**/dist/**/*", "**/node_modules/**/*"],
  "references": [{ "path": "../../workflow/tsconfig.build.esm.json" }]  // ✅ Referencias a dependencias
}
```

**NO hay error**. Solo necesitas las extensiones arriba para que VS Code lo entienda bien.

## 🚀 Instalación Rápida

Command Palette (Ctrl+Shift+P):
```
ext install Vue.volar dbaeumer.vscode-eslint esbenp.prettier-vscode biomejs.biome usernamehw.errorlens eamodio.gitlens
```

O vía terminal:
```bash
code --install-extension Vue.volar --force
code --install-extension dbaeumer.vscode-eslint --force
code --install-extension esbenp.prettier-vscode --force
code --install-extension biomejs.biome --force
code --install-extension usernamehw.errorlens --force
code --install-extension eamodio.gitlens --force
```

Luego recarga VS Code: `Ctrl+Shift+P` → "Developer: Reload Window"

