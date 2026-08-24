# Node con TypeScript - TS-Node-dev (preferido)

1. inicializar proyecto
   
```pnpm init
```

2. Instalar TypeScript y demás dependencias
```
pnpm add -D typescript @types/node ts-node-dev rimraf
```
3. Inicializar el archivo de configuración de TypeScript ( Se puede configurar al gusto)
```
pnpm exec tsc --init --outDir dist/ --rootDir src
```

4. Crear scripts para dev, build y start ([Más sobre TS-Node-dev aquí](https://www.npmjs.com/package/ts-node-dev))
```
"scripts": {
  "dev": "tsnd --respawn --clear src/app.ts",
  "build": "rimraf ./dist && tsc",
  "start": "pnpm run build && node dist/app.js"
}
```
