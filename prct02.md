# Práctica 2 - Instalación y configuración de Visual Studio Code
### En este informe se demostrará los pasos realizados para llevar a cabo la práctica.

Como se nos indica, se utilizará Visual Studio Code (VSC) para llevar a cabo las próximas prácticas de la asignaturua. Una vez descargada e instalada el entorno, se instalará la extensión de VSC denominada Remote-SSH para poder realizar la conexión con la máquina virtual de la práctica anterior.

![image](https://github.com/user-attachments/assets/5dd3d547-7906-4ae8-93db-efe85633f9fa)


Ahora, al yo trabajar en Windows, tendremos que hacer ciertos cambios respecto a la guía presentada para poder llevar a cabo la tarea. Abriremos el PowerShell como Administrador y ejecutaremos el comando _notepad C:\Windows\System32\drivers\etc\hosts_. Y añadiremos la IP de la máquina virtual y el nombre de ella.


![image](https://github.com/user-attachments/assets/689a84a4-5e6d-4dc4-b5aa-10750236690c)

Luego deberemos configurar el SSH para que no nos haga falta escribir usuario y host manualmente. *notepad $env:USERPROFILE\.ssh\config*. Y agregaremos la siguiente configuración para poder conectarse.

![image](https://github.com/user-attachments/assets/41e57b3c-4294-4241-84af-a84898642a4f)

Una vez hecho esto, podemos volver a VSC a seguir con la configuración del SSH. Seguiremos con la guía dada y tras hacerla, y haber dado nuestra contraseña; VSC conectará con la máquina virtual. Abriremos el terminal y usaremos el comando hostname para confirmar que hemos conectado a la máquina correspondiente.

![image](https://github.com/user-attachments/assets/504d2bae-4cf3-4ac4-9270-97563f2ed4d0)

Además, añadiremos la extensión Live Share para poder colaborar en tareas de desarrollo en tiempo real. 

![image](https://github.com/user-attachments/assets/2321e216-3d96-4ffd-a3e2-df4ad0e08d96)


Una vez hecho esto, crearemos un directrorio con el nombre del proyecto. Y dentro de el un fichero *package.json*, que va a permitir que gestionemos las dependencias de desarrollo y ejecución del mismo.

![image](https://github.com/user-attachments/assets/4fd2e47b-5944-4e3b-aaa6-adf6c21c03d1)

![image](https://github.com/user-attachments/assets/efdbfa07-bef8-4b31-84ba-af629da1133f)

Y acto seguido instalaremos el compilador de TypeScript y crearemos un fichero denominado tsconfig.json, que tendra las opciones de configuración de dicho compilador. Se editará el contenido para que tenga lo siguiente:

![image](https://github.com/user-attachments/assets/3734feba-790a-49f7-948c-55cda4dd4d85)


El siguiente paso en la práctica será instalar un paquete que nos permitirá detectar cambios realizados sobre ficheros con código fuente en TypeScript. Para poder usar el paquete deberemos cambiar la propiedad *script* del fichero *package.json*, y añadiremos una propiedad que denominaremos *start*.

![image](https://github.com/user-attachments/assets/20e4b107-1b1b-4eea-b8a8-0c830fdf0165)

![image](https://github.com/user-attachments/assets/f1a7e23a-fc32-4e7d-850d-07d53364a160)

Para saber si funciona el compilador, crearemos un fichero de código sencillo en el directorio source. Luego, ejecutraremos el comando *npm start*, que ejecutará el script definido en la propiedad *start* del fichero *package.json*:

![image](https://github.com/user-attachments/assets/71c1a55e-f24f-4ede-9f07-3e1e370ee19c)

![image](https://github.com/user-attachments/assets/2ab978fb-2d8e-4b39-b9f6-9b5d66991c1d)

###Comprobación y resolución de errores en la lógica del código

El próximo paso será instalr in *linter* para comprobar de manera estatica nuestro código fuente.

![image](https://github.com/user-attachments/assets/4b79415c-5607-4cc4-b38b-d55888c73b29)

Luego crearemos un fichero de configuración de ESLint y responderemos a ciertas preguntas en torno a la inicialización; indicaremos que nuestro proyecto usará TypeScript y se ejecutará en Node.js.

![image](https://github.com/user-attachments/assets/83feb888-e478-412e-b13b-c1fa24fd0bda)


Para comprobar su correcto funcionamiento, cambiaremos el fichero Hola Mundo creado anteriormente. En el *console.log*, pediremos que imprima directamente, Hola Mundo, obviando la declaración hecha anteriormente. Al ejecutar el comando eslint nos aparecerá este mensaje de error:

![image](https://github.com/user-attachments/assets/342bfaae-9da3-48b4-822e-c37ff77f8206)

Este mensaje se podrá cambiar, ya sea para desactivar los avisos de errores, o que simplemente se queden en un aviso precautorio, como el de la siguiente imagen. 

![image](https://github.com/user-attachments/assets/81966cea-148b-4e15-94fa-e1e71deec938)

![image](https://github.com/user-attachments/assets/e2059e3b-8ae2-4643-ac99-5dc97ab93187)

###Formateo del códgio
Para finalizar, instalaremos el Prettier que será nuestro formateador de código.

![image](https://github.com/user-attachments/assets/2988ce54-203e-419d-84e0-c240eab8473e)

El paso siguiente será desactivar las reglas de formateo de ESLint, para evitar problemas y conflictos con las reglas de Prettier. Modificaremos el fichero *eslint.config.mjs* para ello.

![image](https://github.com/user-attachments/assets/dd538c9c-adbb-4cd7-a3d9-e6da53993c35)

Crearemos un fichero, que contendrá todos los ficheros y directorios que no queremos formatear.

![image](https://github.com/user-attachments/assets/2877e3b9-a59d-46c0-8a30-9a60dcccbea6)

Y por último, comprobaremos que el formateador funciona. Cambiaremos el fichero index, por la siguiente función:

![image](https://github.com/user-attachments/assets/228caca4-a3ad-4e38-8ac6-8ac1ec844630)

Y una vez ejecutada la orden de formatear; veremos cambios en el código del fichero. Siendo notorio el cambio en la declaración de la función add, donde cada uno de sus parámetros han sido ubicados en líneas diferentes.



![image](https://github.com/user-attachments/assets/eeb43d5d-4b57-4d4e-a643-b6c8337eab56)
