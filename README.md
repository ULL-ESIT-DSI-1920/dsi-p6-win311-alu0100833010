# dsi-p6-win311-alu0100833010

_Práctica 6.  VueJS._

## Descripción de la Práctica  dsi-p6-win311.

### ¿Qué es VueJS? 

**VueJS** es un _framework_ progresivo para construir interfaces de usuario. A diferencia de otros frameworks monolíticos,
**Vue** está diseñado desde cero para ser utilizado incrementalmente. La librería central está enfocada solo en la capa de
visualización, y es fácil de utilizar e integrar con otras librerías o proyectos existentes. Por otro lado, Vue también es
perfectamente capaz de impulsar sofisticadas _Single-Page Applications_ cuando se utiliza en combinación con herramientas
modernas y librerías de apoyo. 

* **Vue-CLI**:

**Vue-CLI** (interfaz de línea de comandos de _Vue_) es una herramienta creada por **VueJS** que facilita el rápido desarrollo de
las aplicaciones de _Vue_. Nos permite comenzar un proyecto de inmediato sin tener que preocuparnos de diferentes herramientas de
compilación.

* **Objetivo**:

En esta práctica, vamos a utilizar VueJS y su sistema de componentes para crear una imitación visual del sistema de ventanas
del entorno gráfico de Windows 3.11.

## Comenzando

### 1. Crea un proyecto con VueJS.

Para ello comenzamos creando la estructura del proyecto.

#### Pasos para crear el proyecto.

* **Instalación de Vue-CLI** 

  ```
  // Instalamos vue en nuestro sistema
  npm install -g @vue-cli
  ```
  Comprobamos que se ha instalado correctamente:
  ```
  vue --version
  ```
  
* **VueJS**

  Creamos el repo usando el comando `vue`:
  
  ```
  vue create dsi-p6-win311-alu0100833010
  ```
  Nos situamos en el repo:
   ```
  cd dsi-p6-win311-alu0100833010
  ```

Automáticamente se nos crea una estructura del proyecto:
  
  ![Captura1](src/assets/captures/cap15.png)
 
A diferencia de _Parcel_, para correr el servidor ejecutamos el comando:

```
npm run serve
```

Inicialmente, **VueJS** nos muestra una pantalla de bienvenida.

  ![Captura2](src/assets/captures/capVue.png)
  
* **Producción**
```
npm run build
```

* **Linters**
```
npm run lint
```

See [Configuration Reference](https://cli.vuejs.org/config/).
  
### 2. Código _HTML_.

La estrucutura de `index.html` es la siguiente:

 ![Captura3](src/assets/captures/cap1.png)
 
Por defecto, **VueJS** nos crea un archivo `index.html` muy sencillo que sirve como _plantilla_. **VueJS** añade a este archivo
los elementos que necesita que están dentro de la parte de Vue. 

Debemos tener en cuenta el `<div id="app"></div>`, ya que es el contenedor que va a recibir toda la información proveniente de los 
componentes de Vue. Es donde se monta toda la aplicación.

### 3. Código _Javascript_.

Utilizando **VueJS**, creamos los componentes **Win311Window** y **Win311Icon**:

 ![Captura4](src/assets/captures/cap2.png)
 
* `main.js`:

 ![Captura5](src/assets/captures/cap14.png)
 
Sería equivalente al `index.js` que hemos utilizado en las prácticas anteriores. Contiene el núcleo de la parte de **VueJS**. En
este archivo se importa la librería Vue y el fichero `App.vue` que corresponde con el _componente_ principal de la aplicación. 

```
new Vue({
  render: h => h(App)
}).$mount('#app')
```
Se crea una instancia de Vue que es la que utilizará la aplicación y le indica donde ha de montarla, en este caso, en el
elemento _HTML_ con el mismo nombre que vimos en `index.html`. 

### 4. Componentes.

Una de las características más importantes de Vue es el trabajo con componentes. Un componente de _Vue_ es un elemento que 
encapsula código reutilizable. Dentro de un componente podemos encontrar etiquetas _HTML_, estilos de _CSS_ y código _Javascript_.

Antes de ver el código de la práctica, un componente simple de _Vue_ posee 3 secciones: _HTML_, _CSS_ y _Javascript_:
```
<template>
  <h1 class="text"> Plantilla de Vue </h1>
</template>

<script>
</script>

<style>
</style>
```
* `App.vue`:

![Captura6](src/assets/captures/cap3.png)
 
`App.vue` es el componente principal de toda la aplicación. Como mencionamos antes, la estructura del archivo está dividida en
`<template></template>`, `<script></script>` y `<style></style>`.

En `<template></template>` se encuentra el código _HTML_ de la página. Solo debe haber un único elemento hijo, en este caso, 
`<div id="app"></div>`. Dentro de él, encontramos las etiquetas correspondientes con el resto de componentes de la aplicación, 
`<win311-icon>` y `<win311-window>`, en el que a ambos se les indica una prop que hace referencia a `windows.json`, que es un
_json_ que lo que hace es especificar que título y que iconos va a tener cada ventana.

Por otro lado, en `<script></script>`, damos nombre al componente principal e indicamos los componentes locales que tenemos.

![Captura7](src/assets/captures/cap4.png)

Dentro `<style></style>`, se encuentra el código _CSS_ para darle estilo a toda la página.

* `Win311Window.vue`:

Contiene la estructura de la ventana que vamos a crear.  

![Captura8](src/assets/captures/cap5.png)

En _template_, tal y como comentamos antes, solo hay un único elemento hijo, `window`. En él, seccionamos mediante el uso de
_divs_ la estructura de nuestra ventana. 

* * `header`: Añadimos el guión, el título de la ventana y la flecha.

* * `container`: Añadimos la barra de navegación y los iconos de la ventana. En **VueJS** podemos crear componentes más complejos
  que nos permiten renderizar variables, iterar e incluso realizar condicionales. Por tanto, hacemos uso de dicha funcionalidad
  en la etiqueta `<win311-icon>` para generar los iconos y asignar dicha "zona" para ellos.
  
* * `footer`: Añadimos el texto.
  
![Captura9](src/assets/captures/cap6.png)

En _script_ indicamos el componente local `Win311Icon`. También, definimos las `props` y `data` que contiene las variables.  

![Captura10](src/assets/captures/cap7.png)

Y en _style_ definimos el estilo para el componente. Debería haber hecho uso de la propiedad `scoped` para asegurar que dichos 
estilos _CSS_ se apliquen únicamente sobre el componente actual.

* `Win311Icon.vue`:

Componente donde se generan los iconos.

![Captura13](src/assets/captures/cap10.png)

A través del _div_ que contiene a la clase `icon`, llamamos a los métodos `bg_blue` al hacer click y `alert` al hacer doble click.
En `<img>`, mostramos las imágenes de los iconos que se encuentran en _/assets/icons/nombre-icono.png_ y añadimos el nombre y el
color de fondo del mismo.

![Captura14](src/assets/captures/cap11.png)

Declaramos las `props` y en `data` declaramos las variables, exactamente igual que en el componente _Win311Window_. Creamos las 
funciones `bg_blue()` y `alert()`.

  * * `bg_blue`: Cuando el usuario interactúe con el icono y haga click sobre el, ponemos el fondo del nombre del icono en azul.
  Con la variable aux controlamos el número de clicks del usuario.
  
  * * `alert`: Cuando el usuario haga doble click sobre el icono, lanza una alerta con `"Open " + nombre del icono`.
  
En este componente no definimos ningún estilo.
  
### 5. Publicación en _gh-pages_.
 
Para publicar nuestro proyecto en **gh-pages**, como ya no estamos haciendo uso de _Parcel_, cambia la forma. Por tanto, para
hacerlo con _Vue-cli_ creamos el script `deploy.sh`:

![Captura15](src/assets/captures/cap12.png)

y `vue.config. js`:

![Captura16](src/assets/captures/cap13.png)

Al ejecutar `deploy.sh`, ya quedaría nuestro proyecto publicado en **gh-pages**:

![Captura17](src/assets/captures/cap16.png)

Enlace:  https://ull-esit-dsi-1920.github.io/dsi-p6-win311-alu0100833010/

### 6. Retos.

#### Reto 1.

Método: 
```
bg_blue: function(event) {
            if (this.aux === 0) {
                this.aux++;
                this.color = "blue";
            } else {
                this.color = "none";
                this.aux = 0;
            }
```
Llamada:
```
<div class="icon" @click="bg_blue()" @dblclick="alert()">
```
#### Reto 3. 

Método:
```
alert: function(event) {
            alert("Open " + this.name);
        }
```
Llamada:
```
<div class="icon" @click="bg_blue()" @dblclick="alert()">
```
