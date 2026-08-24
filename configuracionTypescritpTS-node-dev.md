# Node con TypeScript - TS-Node-dev (preferido)

1. inicializar proyecto
```
pnpm init
```

2. Crear un archivo en la raiz de proyecto llamado .npmrc
```
# Desactiva la ejecución de scripts maliciosos durante la instalación (preinstall/postinstall)
ignore-scripts=true

# Guarda las dependencias con su versión exacta (sin ^ ni ~)
save-exact=true

minimum-release-age = 1440
block-exotic-subdeps = true
trust-policy = no-downgrade
# node-options = "--permission"
```

3. Instalar TypeScript y demás dependencias
```
pnpm add -D typescript @types/node tsx rimraf
```
4. Inicializar el archivo de configuración de TypeScript ( Se puede configurar al gusto)
```
pnpm exec tsc --init --outDir dist/ --rootDir src
```

5. Crear scripts para dev, build y start ([Más sobre TS-Node-dev aquí](https://www.npmjs.com/package/ts-node-dev))
```
"scripts": {
  "dev": "tsx watch src/app.ts",
  "build": "rimraf ./dist && tsc",
  "start": "pnpm run build && node dist/app.js"
}
```




6. configuracion archivo tsconfig.json se agrega esta configuracion
```
{
  "compilerOptions": {
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "verbatimModuleSyntax": true
  }
}

```

7. configuracion archivo package.json  validamos y agregamos 
```
{
  "name": "tu-proyecto",
  "version": "1.0.0",
  "type": "module", // se agrega solo esta linea
  "scripts": { ... }
}

```

