# Prueba Tecnica Todo Legal

Esta es una prueba tecnica Frontend con una conexion a servicio web utilizando Vue.Js

## Requisitos

-Vue.Js
-Conexion API.
-Funciones de carga, visualizacion y eliminacion de archivos.

### Clona el Repositorio

```bash
https://github.com/Andrxstr/todoLegal.git
```

### Ejecucion del Proyecto

npm run serve

### Acceder a la aplicacion por medio del navegador

Abrir el navegador y acceder a http://localhost:PUERTO, donde el Puerto por defecto suele ser el 8080.

### Estrutura del Proyecto

- src/: Contiene los archivos fuente de la aplicacion
    -assets/: Contiene las imagenes utilizadas en el proyecto
    -components/: Contiene cada uno de los componentes utilizados en la aplicacion
    -App.vue: Contiene el template principal e invoca los demas componentes
    -main.js: importa el App.vue y monta la aplicacion
-README.md: Este contiene detalles del proyecto
-vue.config.js: Contiene la configuracion del proyecto con Vue CLI

### Conexion al servicio Web

Para la conexion web se instalo y utilizo axios.

La conexion al servicio web principalmente se da en el componente de "ButtonNext.vue", pero el link de acceso para el post se encuentra en el componente principal "App.vue", como un parametro editable.

En este se encuentra un link de servicio web comentado, pues el acceso ya habia caducado o se habia elimiando el servicio por lo cual cree uno nuevo que es el link activo al cual realizo el envio de la informacion, para observar el envio de manera correcta se puede observar en la consola del navegador, o creando un nuevo servicio y activando el "CORS Headers", para que el envio no tenga ningun problema.

###  Adaptacion visual

Se realizo la adaptacion de la aplicacion para que este se vea de manera similar tanto en computadoras de escritorio como en dispositivos moviles.

### Validaciones

El aplicativo tiene las siguientes validaciones:
    
    -Solo permite archivos de formato PDF
    -Que el area o seccion donde se cargan o arrastran los archivos, no se puedan cargar mas de 5 archivos
    -Que el tamaño de los archivos no exceda las 20 Mb

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
