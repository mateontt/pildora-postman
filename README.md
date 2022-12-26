<img src="./resources/postmannewman.png" align="center">

<h4 align="center">Pildora sobre como utilizar Postman y Newman.</h4>

<p align="center">
  <img src="https://img.shields.io/badge/-NTT%20DATA-blue" alt="NTT DATA">
  <img src="https://img.shields.io/badge/-Postman-green" alt="Postman">
  <img src="https://img.shields.io/badge/-Newman-orange" alt="Newman">
<p>

<p align="center">
  <a href="#propósito">Propósito</a> •
  <a href="#entorno">Entorno</a> •
  <a href="#download">Postman</a> •
  <a href="#credits">Newman</a> •
  <a href="#license">License</a>
</p>

<hr>

# Propósito

El propósito de la píldora es el de intentar establecer una base para poder utilizar eficázmente Postman y Newman de forma conjunta o separada.

# Entorno

<img src="./resources/icon_container.png" align="right" alt="Container icon" width="130" height="130">

El entorno de pruebas está basado en la popular **PetStore** que estará montada sobre Docker, el cual permite crear todas las instancias necesarias de la PetStore variando únicamente el puerto de conexión.

Se puede utilizar tanto **[Docker Desktop]** como **[Rancher]**.

<br><br>

### Crear contenedores

```bash
# Crear petstore en puerto 88
$ docker run -d --name petstore1 -e SWAGGER_HOST=http://petstore.swagger.io -e SWAGGER_URL=http://localhost -e SWAGGER_BASE_PATH=/v2 -p 88:8080 swaggerapi/petstore

# Crear petstore en puerto 8088
$ docker run -d --name petstore1 -e SWAGGER_HOST=http://petstore.swagger.io -e SWAGGER_URL=http://localhost -e SWAGGER_BASE_PATH=/v2 -p 8088:8080 swaggerapi/petstore
```
<br>

> **Parámetros**
> * `-d` indica que el contenedor se ejecutará en segundo plano liberando la consola
> * `--name` indicará el nombre del contenedor. Tiene que ser único
> * `-e` especifica las variables de entorno que se utilizará el contenedor.
> * `-p 88:8080` especifica el puerto_externo:puerto_interno. En este caso podremos acceder a PetStore mediante la url `http://localhost:88`

<br>

<img src="./resources/dockerconsole.png" align="center">

<br>

Una vez creados los contenedores podremos comprobar que se han creado con éxito si abrimos la URL `http://localhost:88`

<img src="./resources/swagger_homepage.png" align="center">

<br><br>

> **Nota**
> Para que muestre el contenido del Swagger hay que indicar el puerto correctamente en la caja superior, en caso contrario irá a buscar la url al puerto 80 en lugar del 88


# Postman

## Colecciones
Una colección es un conjunto de carpetas y requests. Las carpetas pueden contener scripts que se lanzarían antes de las requests y tests adicionales.

### Crear Requests
* Pulsar sobre el icono de los tres puntos y luego **Add Requests**
<img src="./resources/postman_addrequest.png" align="center">

* Definir un nombre, una acción y la dirección URL del endpoint
<img src="./resources/postman_addrequest_details1.png" align="center">

## Entornos

Los entornos se usan para definir diferentes URL para un mismo servicio según el ambiente (PRE, PRO...) de forma que una misma request pueda ser ejecutada en varios ambientes sin hacer cambios.

Para crear un nuevo ambiente pulsamos en **New**, en la ventana que aparece seleccionamos **Environment**
<img src="./resources/env_newenvironment.png" align="center">
<img src="./resources/env_newenvironment2.png" align="center">
<br><br>
Una vez creado hay que definir los endpoints que contendrá. En este caso se define una variable *port* que contendrá el puerto del endpoint y otra variable llamada *baseUrl* que contendrá la URL utilizando la variable port.

<img src="./resources/env_editenvironment.png" align="center">
<br><br>
Para que la request pueda hacer uso de las variables definidas en el entorno habrá que llamar a *baseUrl*
<img src="./resources/req_variableurl.png" align="center">


## Autenticación

## Variables Globales y de Colección

Las variables se pueden utilizar para reutilizar llamadas, payloads, tests... Se pueden definir en las Colecciones y en los Environments.

Para utilizar una variable se la llamará utilizando doble llave y el nombre: **{{nombre_variable}}**
## Tests

## Runner

## Exportar



# Newman




[Docker Desktop]:https://www.docker.com/products/docker-desktop/
[Rancher ]:      https://rancherdesktop.io/

[GitHub action]: https://github.com/andresz1/size-limit-action
[Statoscope]:    https://github.com/statoscope/statoscope
[cult-img]:      http://cultofmartians.com/assets/badges/badge.svg
[cult]:          http://cultofmartians.com/tasks/size-limit-config.html