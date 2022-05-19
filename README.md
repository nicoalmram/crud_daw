# CrudDaw

En este proyecto hemos realizado una aplicación en Angular con funciones CRUD haciendo uso de servicios, enrutamiento y navegación conectándonos a una base de datos con Firebase.


## Preparación del proyecto

Para poder comenzar, primero creamos un proyecto al que llamaríamos "crud_daw" mediante el comando 'ng new crud_daw' al que aceptamos el routing de Angular y archivos .CSS para el estilo y, además, nos creamos un proyecto en Firestore de Firebase el cual enlazaremos más adelante con nuestra app. A continuación, ejecutaremos el comando 'npm i bootstrap firebase @angular/fire' para instalar los paquetes necesarios:

- bootstrap para añadir estilos
- firebase, instalación necesaria para poder usar Firebase
- @angular/fire para poder interactuar entre nuestro frontend de nuestra aplicación en Angular y el backend en Firebase.

Además, configuramos los archivos 'angular.json' para poder usar los estilos de bootstrap y 'environment.ts' y 'environment.prod.ts' para la conexión con el proyecto creado previamente en Firebase.


## Conexión a Firebase

En 'app.module.ts' importaremos las clases necesarias para poder trabajar con Firestore y la configuración de Firebase. También referenciaremos a la configuración hecha en los archivos environment, lo que nos permitirá la conexión con la base de datos.


## Implementación de servicios

Según la documentación podemos llegar a la conclusión de que "un servicio es una clase que se encarga de acceder a los datos para servir a los componentes. Estos servicios se pueden reutilizar para distintos componentes."
Una vez aclarado esto, hemos generado un servicio con el siguiente comando 'ng generate service post --skip-tests' generando un archivo llamado 'post.service.ts'. En este archivo importaremos los módulos para trabajar con Firestore y nuestro modelo ('Post' en nuestro caso). Además, crearemos y desarrollaremos los métodos que usaremos para nuestro CRUD, los cuales son:

-getPosts(): nos devolverá todos los documentos.
-getPostById(): nos devolverá un único elemento.
-createPost(): creará un elemento.
-updatePost(): actualizará un elemento.
-deletePost(): eliminará un elemento


##Elementos CRUD

Para terminar de implementar las funciones CRUD, crearemos los componentes 'show', 'edit' y 'create'.
- show: La página principal donde se nos mostrará una tabla con todos los datos almacenados hasta el momento en nuetsro proyecto de Firestore con enlaces a la página de create y edit, de delete no hará falta página ya que es más que suficiente disponer de un botón en esta página que se encargue de borrar el elemento seleccionado.
- edit: Nos mostrará un formulario con los datos del elemento seleccionado y podremos sobreescribirlos para actualizar dicho elemento.
- create: Página para crear un nuevo elemento en la que se nos mostrará un formulario a rellenar con los datos deseados y un botón de confirmación que no se activará hasta haber rellenado todos los datos.


## Enrutamiento y navegación

Para poder hacer uso de los elementos CRUD en nuestra aplicación, necesitaremos configurar correctamente las rutas, para ello, haremos uso del routing de Angular mediante el archivo 'app-routing.module.ts'. A este archivo le importaremos nuestros componentes (show, create y edit) para los cuales configuraremos el path correcto para cada uno de los componentes. Una vez hecho esto, cada vez que queramos acceder a alguna de las páginas de nuestros componentes, deberemos hacer referencia al path del componente deseado mediante el uso de '<router-outlet></router-outlet>' en 'app.component.html' (la página principal de nuestra app, y 'routerLink' para movernos entre páginas
