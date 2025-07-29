# Package manager в наших проектах

В наших любимых проектах мы зачастую используем package manager'ы, такие как _npm_, _yarn_, _pnpm_ или _bun_. Важно чтобы в проекте был только один. Мы не должны допускать ситуации, когда в проекте несколько lock файлов, например _package-lock.json_ и _yarn.lock_. Наличие нескольких lock файлов может привести к проблемам. Давайте разберем почему:

```
...
package.json
package-lock.json - npm
```

Когда мы работаем в команде, важно использовать один package manager и в наших скриптах:

```json
"scripts": {
  "dev": "npm run dev",
  "build": "npm run build"
}
```
