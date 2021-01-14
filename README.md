# ⚡ Hello World de Maven

#Workshop

El día de hoy aprenderemos a usar Maven pues es casi un estandar en la construcción de proyectos en Java. Una de las principales ventajas es el manejo de dependencias como JUnit los cuales nos sirven para usar testeo, y otras dependencias que se encuentran en MavenRepository. Todo esto de forma centralizada en un documento llamado POM.xml

## 📦 ¿Como instalar Maven?
Uno de los pocos requesitos necesarios para usar **Maven** es que debes tener instalado Java JDK en el sistema (lo cual puedes comprobar corriendo el comando `java --version`). 

Maven puede ser descargado aqui: [Descargar Maven](https://maven.apache.org/download.cgi).
> El archivo que necesidas descargar se llama Binary Zip Achieve 

Y finalmente necesitarás definir la variable de entorno.

1. Primero deberás descomprimir tu archivo en una ruta donde desees tenerlo (recuerda que no deberás mover ese archivo de ahi después).
2. Para esto tendrás que primero entrar a la **configuración avanzada del sistema**.
3. Luego deberás asegurarte de tener la variable `JAVA_HOME` definida.
4. Ahora deberás crear dos variables nuevas ambas apuntando hacia la misma dirección donde dejaste tu descarga de maven. En mi caso es en `C:\Users\User\.maven\apache-maven-3.6.3\`. 
5. Por último deberás editar la variable `Path` añadiendole una nueva ruta apuntando hacia `%M2_HOME\bin` que es el binario de Maven.

En caso de que (seas alguein genial) y estes usando un sistema Linux (O WSL) puedes instalar maven con tu gestor de paquetes:

- Ubuntu (Derivados como Mint, PopOS o Elementary):
  - `sudo apt install mvn`
- Arch (Manjaro):
  - `sudo pacman -S mvn` 

## ✏ Crear un proyecto con Maven
Primero debemos crear una carpeta donde crear nuestro proyecto y dirigirnos a ella desde nuestra terminal.

Una vez dentro de nuestra carpeta podemos comenzar a correr nuestros comandos de maven (Siempre se usa `mvn` para correr maven en la terminal).

Según la guia rápida de maven [que puedes leer aqui](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html), nosotros podemos utilizar este comando para iniciar un proyecto con toda la estructura de Maven:

```shell
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app
```
La cual lucirá de la siguiente manera:

```
my-app
|-- pom.xml
`-- src
    |-- main
    |   `-- java
    |       `-- com
    |           `-- mycompany
    |               `-- app
    |                   `-- App.java
    `-- test
        `-- java
            `-- com
                `-- mycompany
                    `-- app
                        `-- AppTest.java
```
Donde `archetype:generate` indica que estamos creando un nuevo proyecto. `-DgroupId=com.mycompany.app` define la estructura de tu proyecto (principalmente como se diferencia con otros) mientras que `-DartifactId=my-app` genera el nombre de nuestro compilado.

Por supuesto que todo el comando nos comenzará a pedir una cantidad increible de información, por lo que podemos pasarle el parametro `-DinteractiveMode=false` para que desactive el modo interactivo y tome todos los valores por defecto.

Y finalmente otro de los comandos que pueden resultar de utilidad es el ` -DarchetypeArtifactId=maven-archetype-quickstart` con el que le puedes indicar que tipo de aplicación quieres desarrollar. Puedes leer sobre los tipos de aplicaciones con más detenimiento [aqui](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html)

## ⚙ Compilar con Maven

Una de las muchas ventajas que nos da Maven es la posibilidad de compilar y empaquetar nuestros proyectos. Podemos usar esta característica con el siguiente comando:

```sh
mvn compile
```

Esto nos generará una carpeta llamada *target* donde tendremos nuestras clases y nuestros archivos compilados del proyecto. Ahora, si lo que queremos es obtener el archivo ejecutable (`jar`) del proyecto, entonces necesitaremos usar el siguiente comando:

```sh
mvn package
```

Ahora, para poder limpiar nuestra carpeta target, debemos usar el siguiente comando:

```sh
mvn clean
```