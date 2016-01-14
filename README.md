<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">Instalación de git</a></li>
<li><a href="#orgheadline2">GitHub</a></li>
<li><a href="#orgheadline3">Crear un repositorio</a></li>
<li><a href="#orgheadline4">Clonar un repositorio</a></li>
<li><a href="#orgheadline5">Crear un repositorio</a></li>
<li><a href="#orgheadline6">Estado del repositorio</a></li>
<li><a href="#orgheadline7">Información de cambios en el repositorio</a></li>
<li><a href="#orgheadline9">Añadir y modificar documentos</a>
<ul>
<li><a href="#orgheadline8">Añadir</a></li>
</ul>
</li>
<li><a href="#orgheadline10">Renombrar archivos o directorios</a></li>
<li><a href="#orgheadline11">Actualizar repositorio</a></li>
<li><a href="#orgheadline12">Pull request</a></li>
<li><a href="#orgheadline13">Bibliografía</a></li>
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

# GitHub<a id="orgheadline2"></a>

-   Crea una [cuenta en GitHub](http://www.github.com)
-   Windows: <http://windows.github.com>
-   Mac OS X: <http://mac.github.com>

# Crear un repositorio<a id="orgheadline3"></a>

Primero comprobamos que se ha instalado git con la opción `--version`

    git --version

Luego iniciamos el repositorio con la opción `init`:

    git init

Y comprobamos su estado con la opción `status`:

    git status

Si listamos el directorio, comproboremos que tenemos un directorio oculto llamado `.git`

    ls -la

Cuando quieras que el directorio deje de ser un repositorio Git, tan solo hay que borrar este directorio oculto con `rm -rf`:

    rm -rf .git

Si en este caso podríamos saber el *status* de git, el mensaje nos avisaría diciendo que no se trata de un repositorio git.

# Clonar un repositorio<a id="orgheadline4"></a>

Si queremos realizar una página web, podemos clonar el proyecto Boilerplate de Paul Irish:

    $ git clone git://github.com/paulirish/html5-boilerplate.git

# Crear un repositorio<a id="orgheadline5"></a>

-   Creas un repositorio con un nombre en Github.
-   Github te sugiere varias formas de copiarlo en local, en el propio ordenador. Os recomiendo seguir estos pasos:

    echo "# Proyecto de ..." >> README.md
    git init
    git add README.md
    git commit -m "primer commit"
    git remote add origin https://github.com/tu_usuarix/nombre_proyecto.git
    git push -u origin master

# Estado del repositorio<a id="orgheadline6"></a>

Podemos ver el estado del repositorio con la opción `clone`

    git log

Que nos da toda esta información:

-   La lista de cada `commit`
-   El *hash* *SHA1* del *commit*, una cadena única de cada *commit*
-   La autoría
-   El mensaje que describía el cambio

# Información de cambios en el repositorio<a id="orgheadline7"></a>

Si queremos ver los cambios en esta versión, debemos utilizar la opción `diff`:

    git diff

# Añadir y modificar documentos<a id="orgheadline9"></a>

## Añadir<a id="orgheadline8"></a>

    git add ruta-nuevos-archivos
    git commit -m "comentario sobre cambios"
    git push -u origin nueva-rama

# Renombrar archivos o directorios<a id="orgheadline10"></a>

Renombrar un archivo:

    git mv archivo1 archivo2
    git add archivo2
    git push -u origin master

Renombrar un directorio:

    git mv directorio1 directorio2
    git add directorio2
    git push -u origin master

Ver los cambios que vamos a realizar con la opción `-n`, el atajo de `--dry-run`

    git mv -n foldername folderName

Renombrar en sistemas que no distinguen entre mayúsculas y minúsculas, puede dar un error cuando modifiquemos el nombre por caracteres en mayúsculas, por lo qu etendríamos que hacer:

    git mv directorio1 tempname && git mv tempname Directorio2

Borrar un archivo del repositorio sin borrarlo del sistema de directorios local:

    git rm --cached archivo.org

Para borrar un directorio:

    git rm --cached -r directorio

# Actualizar repositorio<a id="orgheadline11"></a>

Si queremos actualizar el repositorio con los cambios que se hayan producido en él, lo haremos con la opción `pull`:

    git pull

# Pull request<a id="orgheadline12"></a>

Para hacer un pull request, primero tenemos que crear una copia del proyecto:

    $ git clone ruta-proyecto.git

Luego creamos una rama donde hacer las modificaciones:

    $ git checkout -b nueva-rama

Al crearla nos movemos a esa rama. Podemos comprobarlo si tenemos el asterisco en la rama deseada:

    $ git branch

Si no estamos ahí, vamos con:

    $ git checkout nueva-rama

Luego hacemos las modificaciones que sean a nuestros archivos, las añadimos, las comiteamos y las subimos a la rama creada:

    git add ruta-nuevos-archivos
    git commit -m "comentario sobre cambios"
    git push -u origin nueva-rama

Comprobamos el estado de git con `git status`

Si todo está bien, vamos a github y en la página del repo pondrá que hay una rama sobre la que hacer un pull-request: pinchamos y seguimos los pasos.

Si no hay discusión, si está todo bien, el administrador lo aprobará y entonces podremos borrar la rama. Nos movemos a master y desde ahí borramos en local y en el servidor:

    git checkout master
    git branch -d nueva-rama
    git push origin --delete nueva-rama

# Bibliografía<a id="orgheadline13"></a>

-   <http://alistapart.com/article/get-started-with-git>
-   <http://progit.org/book/ch1-4.html>
