---
title: Create a project in React without create-react-app (Spanish)
date: '2022-03-09'
tags: ['JavaScript', 'React', 'Web', 'Beginner']
draft: false
summary: Comprender lo que se necesita para crear una aplicación de React y los conceptos básicos de agrupación. Tener nociones de como funciona por detrás y tener un cierto control sobre la estructura de la aplicación.
---

## Introducción.

El comando de **create-react-app** nos ahorra mucho tiempo de configuración para iniciar nuestros proyectos en React.

Pero no vamos a usar **create-react-app**, nosotros mismos vamos a crear la configuración de nuestro proyecto desde cero.

Si deseas gestionar tu mismo la configuración de tu proyecto desde cero, entonces puede que esta publicación sea útil para ti.

## Objetivo.

Mi objetivo es que se pueda comprender lo que se necesita para crear una aplicación de React y los conceptos básicos de agrupación.

Tener nociones de como funciona por detrás y tener un cierto control sobre la estructura de la aplicación.

## Herramientas antes de iniciar.

- Un editor de código, puedes usar [VSCode](https://code.visualstudio.com/), [Atom](https://atom.io/) o el editor de tu preferencia.
- Un navegador actualizado.
- Terminal de comandos.
- Tener instalado [Node](https://nodejs.org/en/) y [npm](https://docs.npmjs.com/getting-started).
- Tener instalado [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) y tener una cuenta en [Github](https://github.com/).

## 1. Crear Repositorio en Github.

Primero vamos a crear un nuevo repositorio en Github.
![imagen de repositorio](https://res.cloudinary.com/practicaldev/image/fetch/s--wTfQXmZn--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/p4hf744mq3591ao24sbm.png)

- Agregamos un nombre.
- Agregamos una descripción.
- Seleccionamos publico, esto para poderlo compartir con la comunidad.
- Damos clic para inicializar un README en nuestro proyecto.
- Agregamos un archivo .gitignore con configuración Node.
- Agregamos una licencia MIT, para indicar que nuestro código es libre y que otros desarrolladores puedan utilizarlo y modificarlo

Después de crear nuestro proyecto vamos a clonarlo.

![clonar repositorio](https://res.cloudinary.com/practicaldev/image/fetch/s--spVNT-Kp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/wbqy2o087nzqhg1oxwgu.png)

Vamos a nuestra terminal, elegimos nuestro directorio para clonar nuestro proyecto.

## Utilizamos el comando:

```
git clone URL_REPOSITORIO
```

## 2. Iniciar proyecto, instalación de React y ReactDOM.

**Utilizamos el comando:**

```
npm init -y
```

Se crea nuestro **package.json** con una configuración por defecto.

```
{
  "name": "curriculumvitae",
  "version": "1.0.0",
  "description": "- Crear un proyecto desde 0 con React JS.",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/AlfredoCU/curriculumvitae.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/AlfredoCU/curriculumvitae/issues"
  },
  "homepage": "https://github.com/AlfredoCU/curriculumvitae#readme"
}
```

Ahora vamos a instalar React y ReactDOM con el **siguiente comando:**

```
 npm install react react-dom --save
```

## Paquetes instalados:

```
+ react-dom@16.13.1
+ react@16.13.1
added 8 packages from 3 contributors and audited 22 packages in 2.845s
found 0 vulnerabilities
```

Nota: es importante observar que las versiones de estos paquetes se encuentren con cero vulnerabilidades para evitar problemas en producción.

## 3. Instalación y configuración de Babel.

[Babel](https://babeljs.io/) es una herramienta que nos ayuda a transpilar nuestro código React y JavaScript modernos a un código JavaScript que pueda entender los navegadores.

Vamos añadir babel a nuestro proyecto con el **siguiente comando:**

```
npm install @babel/core @babel/preset-env @babel/preset-react babel-loader --save-de
```

## Paquetes instalados:

```
+ @babel/preset-react@7.9.4
+ babel-loader@8.1.0
+ @babel/core@7.9.0
+ @babel/preset-env@7.9.5
added 174 packages from 83 contributors and audited 2091 packages in 25.106s
found 0 vulnerabilities
```

Ahora vamos a instalar un plugin para transpilar clases o funciones flecha en funciones normales.

## Utilizamos el comando:

```
npm install babel-plugin-transform-class-properties --save-dev
```

## Paquetes instalados:

```
+ html-webpack-plugin@4.2.0
+ webpack@4.42.1
+ html-loader@1.1.0
+ webpack-cli@3.3.11
added 458 packages from 303 contributors and audited 7546 packages in 109.415s
found 0 vulnerabilities

```

Vamos a escribir la configuración de Webpack en un archivo en la raíz del proyecto llamado webpack.config.js, puedes aprender más sobre cómo configurar estos archivos en: [Webpack](https://webpack.js.org/configuration)

```
const path = require("path");
const HtmlWebPackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
  },
  resolve: {
    extensions: [".js", ".jsx"],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
        },
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
          },
        ],
      },
    ],
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./public/index.html",
      filename: "./index.html",
    }),
  ],
};

```

## 5. Estructura del proyecto.

Vamos a crear la estructura de nuestro proyecto.

- Crear la carpeta src/ para guardar nuestro código JavaScript.
- Crear la carpeta public/ para archivos estáticos de nuestro proyecto como index.html, iconos, imágenes, etc.
- El archivo src/index.js será el archivo principal de JavaScript donde vamos a importar el resto de componentes y contenedores de nuestra aplicación.
- Vamos a crear nuestros componentes en la carpeta src/components y los contenedores de estos componentes en la carpeta src/containers.

![Estructura de archivos](https://res.cloudinary.com/practicaldev/image/fetch/s--eg0w0Ip0--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/dw3eyrzy9bsa6rhtrokp.png)
Nota: Todos nuestros componentes deben comenzar con una letra mayúscula a pesar de que los archivos sigan alguna otra convención.

Debemos de verificar que la carpeta **node_modules/** se encuentre en el archivo **.gitignore** para no subirlo a Github ni a producción porque es una carpeta muy pesada y puede dañar nuestro proyecto.

También agregar la carpeta **dist/** en el archivo **.gitignore**, esta carpeta almacenara la compilación de nuestro proyecto.

## 6. Creando nuestros archivos.

Ya esta hecha la estructura de nuestro proyecto, vamos a crear un componente llamado **src/components/About.jsx** lo cual sólo nos mostrara un "Hola Mundo".

```
import React from "react";

const About = () => {
  return (
    <div>
      <h1> Hola Mundo! </h1>
    </div>
  );
};

export default About;
```

Creamos un archivo **src/index.js**, vamos añadir nuestro componente para después enviarlo a nuestro archivo index.html.

```
import React from "react";
import ReactDOM from "react-dom";
import About from "./components/About";

ReactDOM.render(<About />, document.getElementById("app"));
```

Creamos un archivo **public/index.html** hacemos la referencia por medio del id "app" para que busque y empujar nuestra aplicación.

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>React</title>
    </head>
    <body>
        <div id="app"></div>
    </body>
</html>
```

## 7. Creando nuestro servidor local.

Vamos a usar **Webpack Dev Server** para crear un servidor local que nos permita visualizar los cambios de nuestro proyecto en tiempo real, es decir, sin recargar el navegador.

## Utilizamos el comando:

```
npm install webpack-dev-server --save-dev
```

## Paquete instalado:

```
+ webpack-dev-server@3.10.3
added 175 packages from 117 contributors and audited 11142 packages in 31.689s
found 0 vulnerabilities
```

También, vamos a crear dos nuevos **scripts** en nuestro **package.json.**

- **build** para compilar nuestro proyecto (para producción).
- **start** para iniciar un servidor con **live reload** en el puerto 8080 (para desarrollo).

```
"scripts": {
  "start": "webpack-cli serve --open --mode development",
  "build": "webpack --mode production",
  "test": "echo \"Error: no test specified\" && exit 1"
}
```

Puedes encontrar más información sobre Webpack Dev Server y Live Reload en: [webpack](https://webpack.js.org/configuration/dev-server/)

## Utilizamos el comando:

```
npm run build
```

Nos creara una carpeta llamada **dist**, donde almacena la compilación del proyecto:

```
...
Hash: 9769c65335e6604e9abb
Version: webpack 4.42.1
Time: 5643ms
Built at: 2020-04-15 21:49:06
       Asset       Size  Chunks             Chunk Names
./index.html  226 bytes          [emitted]
   bundle.js    128 KiB       0  [emitted]  main
..
```

Estructura final del proyecto.
![Estructura final del proyecto.](https://res.cloudinary.com/practicaldev/image/fetch/s--lL63z4lD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/u9a5huhii0l70uvjjx67.png)

## Utilizamos el comando:

```
npm run start
```

## Corre nuestro servidor:

```
...
ℹ ｢wds｣: Project is running at http://localhost:8080/
ℹ ｢wds｣: webpack output is served from /
...
```

¡Listo!
![Hola mundo React](https://res.cloudinary.com/practicaldev/image/fetch/s--WzrLXizC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/nrmog1o3436b7oui6ogh.png)
