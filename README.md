<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">Instalación de git</a></li>
<li><a href="#orgheadline2">GitHub</a></li>
<li><a href="#orgheadline3">Llave SSH</a></li>
<li><a href="#orgheadline4">Configuración</a></li>
<li><a href="#orgheadline11">Crear un repositorio</a>
<ul>
<li><a href="#orgheadline8">Opción GitHub al final</a>
<ul>
<li><a href="#orgheadline5">Nuevo repositorio en directorio nuevo</a></li>
<li><a href="#orgheadline6">Nuevo repositorio en directorio existente</a></li>
<li><a href="#orgheadline7">Pasarlo a GitHub</a></li>
</ul>
</li>
<li><a href="#orgheadline9">Opción GitHub</a></li>
<li><a href="#orgheadline10">Comprobaciones</a></li>
</ul>
</li>
<li><a href="#orgheadline12">Clonar un repositorio</a></li>
<li><a href="#orgheadline13">Estado del repositorio</a></li>
<li><a href="#orgheadline14">Información de cambios en el repositorio</a></li>
<li><a href="#orgheadline16">Añadir y modificar documentos</a>
<ul>
<li><a href="#orgheadline15">Añadir</a></li>
</ul>
</li>
<li><a href="#orgheadline22">Renombrar archivos o directorios</a>
<ul>
<li>
<ul>
<li><a href="#orgheadline17">Renombrar un archivo</a></li>
<li><a href="#orgheadline18">Renombrar un directorio</a></li>
<li><a href="#orgheadline19">Case sensitive</a></li>
<li><a href="#orgheadline20">Borrar del repositorio</a></li>
<li><a href="#orgheadline21">Borrar un directorio</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#orgheadline23">Actualizar repositorio</a></li>
<li><a href="#orgheadline24">Pull request</a></li>
<li><a href="#orgheadline25">Bibliografía</a></li>
</ul>
</div>
</div>

Módulo de periodismo de datos de *github* donde aprenderemos cosas directamente relacionadas:

-   git
-   gestión de proyectos
-   crear copias de proyectos
-   adaptar proyectos
-   participar en proyectos.

Puedes trabajar con git desde herramientas gráficas o desde la línea de comandos.

En este caso vamos a trabajar con la línea de comandos, preferiblemente en GNU/Linux.

# Instalación de git<a id="orgheadline1"></a>

En GNU/Linux, tan solo hay que instalar `git-core`:

    apt-get install git-core

En Mac se puede instalar el [instalador gráfico de git](http://code.google.com/p/git-osx-installer) y en Windows, [msysgit](http://code.google.com/p/msysgit/).

Para usar git desde la terminal en Mac hay que activar las funciones de Xcode.

Comprobamos que se ha instalado git con la opción `--version`

    git --version

# GitHub<a id="orgheadline2"></a>

-   Crea una [cuenta en GitHub](http://www.github.com)
-   Windows: <http://windows.github.com>
-   Mac OS X: <http://mac.github.com>

# Llave SSH<a id="orgheadline3"></a>

Puedes conectarte por ssh y activar la llave ssh para conectarte de forma autentificada automáticamente. Si esto que lees no te parece raro y crees que puedes hacerlo, no dejes de leer este manual:
<https://help.github.com/articles/generating-ssh-keys/>

# Configuración<a id="orgheadline4"></a>

La primera vez que usas Git te pedirá tu nombre de correo y de usuario. Lo podemos agregar con el comando `config`.

Añado la dirección de correo electrónico:

    git config --global user.email "usuarix@dominio"

# Crear un repositorio<a id="orgheadline11"></a>

## Opción GitHub al final<a id="orgheadline8"></a>

Podemos iniciar el proyecto git en un directorio cualquiera, ya creado, o bien crearlo en uno nuevo.

### Nuevo repositorio en directorio nuevo<a id="orgheadline5"></a>

Si queremos crearlo en uno nuevo, iniciamos el repositorio con la opción `init` seguida del nombre del directorio:

    git init nombre_repo

### Nuevo repositorio en directorio existente<a id="orgheadline6"></a>

También podemos crear un directorio con `mkdir` y luego inicializar ese directorio solo con la opción `init`:

    mkdir nombre_directorio
    cd nombre_directorio
    git init

### Pasarlo a GitHub<a id="orgheadline7"></a>

Para que el repositorio o proyecto también esté en GitHub, vamos a Github y creamos un proyecto nuevo que llamamos con el nombre del directorio que hemos creado o del directorio que ya existía.

No marques la opción *Initialize with README* y tampoco le asignes licencia, vamos a crear un repositorio vacío para que nos sea más fácil realizar el primer `push`.

Conectamos el directorio local donde nos encontramos con GitHub de la siguiente manera:

    $ git remote add origin https://github.com/tu_nombre_usuarix/primera-newsapp.git

Donde le decimos a `git` que añadimos un `.git` remoto en la URL de GitHub.

## Opción GitHub<a id="orgheadline9"></a>

Primero creas un repositorio con un nombre en Github.

Github te sugiere varias formas de copiarlo en local, en el propio ordenador. Os recomiendo seguir estos pasos:

    echo "# Proyecto de ..." >> README.md
    git init
    git add README.md
    git commit -m "primer commit"
    git remote add origin https://github.com/tu_usuarix/nombre_proyecto.git
    git push -u origin master

## Comprobaciones<a id="orgheadline10"></a>

Comprobamos su estado con la opción `status`:

    git status

Si listamos el directorio, comproboremos que tenemos un directorio oculto llamado `.git`

    ls -la

Cuando quieras que el directorio deje de ser un repositorio git, tan solo hay que borrar este directorio oculto con `rm -rf`:

    rm -rf .git

Si en este caso podríamos saber el *status* de git, el mensaje nos avisaría diciendo que no se trata de un repositorio git.

# Clonar un repositorio<a id="orgheadline12"></a>

Vamos a cualquier proyecto de GitHub y copiamos la URL que aparece en la casilla de **HTTPS**. En este caso, vamos a clonar el proyecto Boilerplate de Paul Irish:

    git clone git://github.com/paulirish/html5-boilerplate.git

# Estado del repositorio<a id="orgheadline13"></a>

Podemos ver el estado del repositorio con la opción `log`

    git log

Que nos da toda esta información:

-   La lista de cada `commit`
-   El *hash* *SHA1* del *commit*, una cadena única de cada *commit*
-   La autoría
-   El mensaje que describía el cambio

# Información de cambios en el repositorio<a id="orgheadline14"></a>

Si queremos ver los cambios en esta versión, debemos utilizar la opción `diff`:

    git diff

# Añadir y modificar documentos<a id="orgheadline16"></a>

## Añadir<a id="orgheadline15"></a>

    git add ruta-nuevos-archivos
    git commit -m "comentario sobre cambios"
    git push -u origin nueva-rama

# Renombrar archivos o directorios<a id="orgheadline22"></a>

### Renombrar un archivo<a id="orgheadline17"></a>

    git mv archivo1 archivo2
    git add archivo2
    git push -u origin master

### Renombrar un directorio<a id="orgheadline18"></a>

    git mv directorio1 directorio2
    git add directorio2
    git push -u origin master

Ver los cambios que vamos a realizar con la opción `-n`, el atajo de `--dry-run`

    git mv -n nombre_directorio_antiguo nombre_directorio_nuevo

### Case sensitive<a id="orgheadline19"></a>

Renombrar en sistemas que no distinguen entre mayúsculas y minúsculas, puede dar un error cuando modifiquemos el nombre por caracteres en mayúsculas, por lo que tendríamos que hacer:

    git mv directorio1 tempname && git mv tempname Directorio2

### Borrar del repositorio<a id="orgheadline20"></a>

Borrar un archivo del repositorio sin borrarlo del sistema de directorios local:

    git rm --cached archivo.org

### Borrar un directorio<a id="orgheadline21"></a>

Para borrar un directorio:

    git rm --cached -r directorio

# Actualizar repositorio<a id="orgheadline23"></a>

Si queremos actualizar el repositorio con los cambios que se hayan producido en él, lo haremos con la opción `pull`:

    git pull

# Pull request<a id="orgheadline24"></a>

Haremos un *pull request* cuando queramos contribuir con nuestros cambios -mejoras, corrección de errores, actualizaciones- a un repositorio que ya existe.

Por eso, lo primero que tenemos que hacer es crear una copia del proyecto:

    $ git clone ruta-proyecto.git

Luego creamos una rama donde hacer las modificaciones:

    $ git checkout -b nueva-rama

Al crearla nos movemos a esa rama. Podemos comprobarlo si tenemos el asterisco en la rama deseada:

    git branch

Si no estamos ahí, vamos con:

    git checkout nueva-rama

Luego hacemos las modificaciones que sean a nuestros archivos, las añadimos, las comiteamos y las subimos a la rama creada:

    git add ruta-nuevos-archivos
    git commit -m "comentario sobre cambios"
    git push -u origin nueva-rama

Comprobamos el estado de git con `git status`

    git status

Si todo está bien, vamos a nuestra copia del proyecto en Github y en la página del repo pondrá que hay una rama sobre la que hacer un *pull-request*, pinchamos y seguimos los pasos.

Si no hay discusión, si está todo bien, el administrador lo aprobará y entonces podremos borrar la rama. Nos movemos a master y desde ahí borramos en local y en el servidor:

    git checkout master
    git branch -d nueva-rama
    git push origin --delete nueva-rama

# Bibliografía<a id="orgheadline25"></a>

-   <http://alistapart.com/article/get-started-with-git>
-   <http://progit.org/book/ch1-4.html>
-   [Qué es y cómo publicar nuestros proyectos en Github](http://ferblape.github.io/github.com-medialab-desigualdad)
