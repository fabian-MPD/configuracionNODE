# configuracionNODE
Los comandos que requerimos   para confugurar Node con TypeScripts
# Pasos para usar Node con TypeScript con Nodemon

Más información - [Docs Oficiales](https://nodejs.org/en/learn/getting-started/nodejs-with-typescript)


0. instala todas las configuraciones de package.json
```
pnpm init
```
1. Instalar TypeScript y tipos de Node, como dependencia de desarrollo
```
pnpm add -D typescript @types/node
```
2. Inicializar el archivo de configuración de TypeScript ( Se puede configurar al gusto)
```
pnpm exec tsc --init --outDir dist/ --rootDir src
```

3. **Opcional** - Para traspilar el código, se puede usar este comando
```
pnpm exec tsc
pnpm exec tsc --watch
```

4. Configurar Nodemon y Node-TS
```
pnpm add -D tsx
```
5. Crear archivo de configuración de Nodemon - **nodemon.json**
```
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "node --loader ts-node/esm ./src/app.ts"
}
```
6. Crear script para correr en desarrollo en el **package.json**
```
  "dev": "nodemon"
  "dev": "pnpm dlx nodemon" // En caso de no querer instalar nodemon
```

7. Instalar rimraf (Herramienta que funciona similar al rm -f) eliminar directorio
```
pnpm add -D rimraf
```

8. Crear scripts en el package.json para construir e iniciar en producción
```
  "build": "rimraf ./dist && tsc",
  "start": "pnpm run build && node dist/app.js"
```
9. en visual estudio si tenemos un error en el archivo tsconfig. en la barra de busqueda buscamos 
```
  Developer: Reload Window
```

10. Crear un archivo en la raiz de proyecto llamado .npmrc
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
