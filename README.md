<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">Instalación de git</a></li>
<li><a href="#orgheadline2">GitHub</a></li>
<li><a href="#orgheadline8">Llave SSH</a>
<ul>
<li><a href="#orgheadline3">Comprobación de claves</a></li>
<li><a href="#orgheadline6">Generar claves ssh</a>
<ul>
<li><a href="#orgheadline4">Copia de clave con método <code>pbcopy</code></a></li>
<li><a href="#orgheadline5">Copia de clave con <code>more</code> y copiar y pegar</a></li>
</ul>
</li>
<li><a href="#orgheadline7">Configuración local y comprobación</a></li>
</ul>
</li>
<li><a href="#orgheadline9">Configuración</a></li>
<li><a href="#orgheadline16">Crear un repositorio</a>
<ul>
<li><a href="#orgheadline13">Opción GitHub al final</a>
<ul>
<li><a href="#orgheadline10">Nuevo repositorio en directorio nuevo</a></li>
<li><a href="#orgheadline11">Nuevo repositorio en directorio existente</a></li>
<li><a href="#orgheadline12">Pasarlo a GitHub</a></li>
</ul>
</li>
<li><a href="#orgheadline14">Opción GitHub</a></li>
<li><a href="#orgheadline15">Comprobaciones</a></li>
</ul>
</li>
<li><a href="#orgheadline17">Clonar un repositorio</a></li>
<li><a href="#orgheadline18">Estado del repositorio</a></li>
<li><a href="#orgheadline19">Información de cambios en el repositorio</a></li>
<li><a href="#orgheadline21">Añadir y modificar documentos</a>
<ul>
<li><a href="#orgheadline20">Añadir</a></li>
</ul>
</li>
<li><a href="#orgheadline27">Renombrar archivos o directorios</a>
<ul>
<li>
<ul>
<li><a href="#orgheadline22">Renombrar un archivo</a></li>
<li><a href="#orgheadline23">Renombrar un directorio</a></li>
<li><a href="#orgheadline24">Case sensitive</a></li>
<li><a href="#orgheadline25">Borrar del repositorio</a></li>
<li><a href="#orgheadline26">Borrar un directorio</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#orgheadline28">Actualizar repositorio</a></li>
<li><a href="#orgheadline29">Pull request</a></li>
<li><a href="#orgheadline30">Borrar rama</a></li>
<li><a href="#orgheadline31">Mantener un repositorio forkeado actualizado</a></li>
<li><a href="#orgheadline34">Publicación web</a>
<ul>
<li><a href="#orgheadline32">Nombre del repositorio</a></li>
<li><a href="#orgheadline33">Rama gh-pages</a></li>
</ul>
</li>
<li><a href="#orgheadline37">Problemas</a>
<ul>
<li><a href="#orgheadline35">403 fatal: HTTP request failed</a></li>
<li><a href="#orgheadline36">git: error: src refspec master does not match any</a></li>
</ul>
</li>
<li><a href="#orgheadline38">Bibliografía</a></li>
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

En Mac se puede instalar el [instalador gráfico de git](https://sourceforge.net/projects/git-osx-installer/) y en Windows, [git for Windows](https://git-for-windows.github.io/).

> Para usar git desde la terminal en Mac hay que activar las funciones de Xcode.

Si queremos disfrutar de una terminal potente, podríamos usar [Cygwin](http://cygwin.com) en Windows o la Terminal en  Mac.

Comprobamos que se ha instalado git con la opción `--version`

    git --version

También tenemos los instaladores oficiales de [git](http://www.git-scm.com):

-   Mac, <http://www.git-scm.com/download/mac>
-   Windows, <http://www.git-scm.com/download/win>

# GitHub<a id="orgheadline2"></a>

Crea una [cuenta en GitHub](http://www.github.com)

Si no te atreviste con el paso anterior, puedes usar estos programas de escritorio para Windows y Mac:

-   Windows: <http://windows.github.com> y [primeros pasos](https://help.github.com/articles/set-up-git/#platform-windows)
-   Mac OS X: <http://mac.github.com> y [primeros pasos](https://help.github.com/articles/set-up-git/#platform-mac)

# Llave SSH<a id="orgheadline8"></a>

> Si no sabes qué es SSH, sáltate esto

Las claves SSH son una forma de identificar ordenadores de confianza sin comprometer contraseñas. Se peude generar unas claves SSH y añadir la clave pública de GitHub para que se produzca la conexión.

GitHub recomienda revisar regularmente la lista de claves SSH y revocar aquellas que no se usen, no se hayan usado o no se vayan a usar.

Puedes conectarte por ssh y activar la llave ssh para conectarte de forma autentificada automáticamente. Vayamos paso a paso.

## Comprobación de claves<a id="orgheadline3"></a>

Primero comprobamos que contamos con clave ssh en el equipo:

    ls -la ~/.ssh

Si aparece un listado de claves, podremos saltarnos el siguiente paso. Si no, debemos generar unas claves.

## Generar claves ssh<a id="orgheadline6"></a>

Necesitas generar una clave ssh el equipo local desde el que te conectas:

    ssh-keygen -t rsa -b 4096 -C "correo-electronico@dominio.com"

Lo cual crea una nueva clave ssh y utiliza el correo electrónico como etiqueta.

Si todo va bien, mostrará el mensaje de generación de la clave, pedirá dónde almacenarla y se puede añadir una contraseña:

    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/usuarix/.ssh/id_rsa): 
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /home/usuarix/.ssh/id_rsa.
    Your public key has been saved in /home/usuarix/.ssh/id_rsa.pub.
    The key fingerprint is:
    (...)

`(...)` es donde aparece la clave.

Ahora que ya tenemos la clave, la pegamos en GitHub en las preferencias, en el apartado "SSH and GPG keys".

### Copia de clave con método `pbcopy`<a id="orgheadline4"></a>

Para seleccionar la clave, podemos emplear el método MacOSX `pbcopy`, que podemos hackear en GNU/Linux con un *alias* a partir de `xsel`:

    alias pbcopy='xsel --clipboard --input'
    alias pbpaste='xsel --clipboard --output'

De esta forma ya podemos utilizar `pbcopy`:

    pbcopy < ~/.ssh/id_rsa.pub

Y pegamos en GitHub. A partir de ahí ya podremos conectarnos con GitHub de forma segura.

### Copia de clave con `more` y copiar y pegar<a id="orgheadline5"></a>

Podemos hacerlo en dos pasos, mostrando la clave y copiándola con el ratón:

    more ~/.ssh/id_rsa.pub

## Configuración local y comprobación<a id="orgheadline7"></a>

Ya está casi todo hecho. Ahora falta decirle a git que nos conectamos a GitHub de forma segura. Para ello, podemos comprobar que lo podemos hacer, y en el mismo paso aprobar la conexión:

    ssh -T git@github.com

Nos pedirá la contraseña que hayamos puesto a la clave si lo hemos hecho, lo introducimos y listo. Si no, nos saldrá directamente el mensaje:

    The authenticity of host 'github.com (192.30.252.1)' can't be established.
    RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
    Are you sure you want to continue connecting (yes/no)?

Nótese que 192.30.252.1 es una de las direcciones IP de GitHub, pero podría salir otra. Lo más importante es fijarse en el fingerprint.

Le decimos que sí y entonces GitHub nos responde:

    Hi usuarix! You've successfully authenticated, but GitHub does not provide shell access.

Donde `usuarix` es nuestrx usuarix en GitHub. Ya está hecho.

Si nos apareciese el mensaje `access denied`, recomiendo seguir los pasos anteriores o [este artículo de GitHub](https://help.github.com/articles/error-permission-denied-publickey) para comprobar que lo hemos hecho bien.

# Configuración<a id="orgheadline9"></a>

La primera vez que usas Git te pedirá tu nombre de usuarix y dirección de correo. Lo podemos agregar con el comando `config`.

Añado el nombre de la cuenta, en este caso el nombre de usuarix en GitHub:

    git config --global user.name "Nombre_de_Usuarix"

Añado la dirección de correo electrónico:

    git config --global user.email "usuarix@dominio"

Si no queremos aplicar esta configuración a todo el sistema y solo a este repositorio porque manejamos más usuarixs de GitHub, por ejemplo, no pongáis la opción `--global`

# Crear un repositorio<a id="orgheadline16"></a>

## Opción GitHub al final<a id="orgheadline13"></a>

Podemos iniciar el proyecto git en un directorio cualquiera, ya creado, o bien crearlo en uno nuevo.

### Nuevo repositorio en directorio nuevo<a id="orgheadline10"></a>

Si queremos crearlo en uno nuevo, iniciamos el repositorio con la opción `init` seguida del nombre del directorio:

    git init nombre_repo

### Nuevo repositorio en directorio existente<a id="orgheadline11"></a>

También podemos crear un directorio con `mkdir` y luego inicializar ese directorio solo con la opción `init`:

    mkdir nombre_directorio
    cd nombre_directorio
    git init

### Pasarlo a GitHub<a id="orgheadline12"></a>

Para que el repositorio o proyecto también esté en GitHub, vamos a Github y creamos un proyecto nuevo que llamamos con el nombre del directorio que hemos creado o del directorio que ya existía.

> No marques la opción *Initialize with README* y tampoco le asignes licencia, vamos a crear un repositorio vacío para que nos sea más fácil realizar el primer `push`.

Conectamos el directorio local donde nos encontramos con GitHub de la siguiente manera:

    git remote add origin https://github.com/tu_nombre_usuarix/primera-newsapp.git

Donde le decimos a `git` que añadimos un `.git` remoto en la URL de GitHub.

Hemos de crear al menos un archivo README.md donde puedes poner la información del proyecto:

    echo "# Otro proyecto ni más ni menos" >> README.md

Añadimos el archivo a git:

    git add README.md

Lo comiteamos:

    git commit -m "mi primer commit"

Y lo subimos a GitHub:

    git push -u origin master

## Opción GitHub<a id="orgheadline14"></a>

Primero creas un repositorio con un nombre en Github.

Github te sugiere varias formas de copiarlo en local, en el propio ordenador. Os recomiendo seguir estos pasos:

    echo "# Proyecto de ..." >> README.md
    git init
    git add README.md
    git commit -m "primer commit"
    git remote add origin https://github.com/tu_usuarix/nombre_proyecto.git
    git push -u origin master

## Comprobaciones<a id="orgheadline15"></a>

Comprobamos su estado con la opción `status`:

    git status

Si listamos el directorio, comproboremos que tenemos un directorio oculto llamado `.git`

    ls -la

Cuando quieras que el directorio deje de ser un repositorio git, tan solo hay que borrar este directorio oculto con `rm -rf`:

    rm -rf .git

Si en este caso podríamos saber el *status* de git, el mensaje nos avisaría diciendo que no se trata de un repositorio git.

# Clonar un repositorio<a id="orgheadline17"></a>

Vamos a cualquier proyecto de GitHub y copiamos la URL que aparece en la casilla de **HTTPS**. En este caso, vamos a clonar el proyecto Boilerplate de Paul Irish:

    git clone git://github.com/paulirish/html5-boilerplate.git

# Estado del repositorio<a id="orgheadline18"></a>

Podemos ver el estado del repositorio con la opción `log`

    git log

Que nos da toda esta información:

-   La lista de cada `commit`
-   El *hash* *SHA1* del *commit*, una cadena única de cada *commit*
-   La autoría
-   El mensaje que describía el cambio

# Información de cambios en el repositorio<a id="orgheadline19"></a>

Si queremos ver los cambios en esta versión, debemos utilizar la opción `diff`:

    git diff

# Añadir y modificar documentos<a id="orgheadline21"></a>

## Añadir<a id="orgheadline20"></a>

    git add ruta-nuevos-archivos
    git commit -m "comentario sobre cambios"
    git push -u origin rama

# Renombrar archivos o directorios<a id="orgheadline27"></a>

### Renombrar un archivo<a id="orgheadline22"></a>

    git mv archivo1 archivo2
    git add archivo2
    git push -u origin master

### Renombrar un directorio<a id="orgheadline23"></a>

    git mv directorio1 directorio2
    git add directorio2
    git push -u origin master

Ver los cambios que vamos a realizar con la opción `-n`, el atajo de `--dry-run`

    git mv -n nombre_directorio_antiguo nombre_directorio_nuevo

### Case sensitive<a id="orgheadline24"></a>

Renombrar en sistemas que no distinguen entre mayúsculas y minúsculas, puede dar un error cuando modifiquemos el nombre por caracteres en mayúsculas, por lo que tendríamos que hacer:

    git mv directorio1 tempname && git mv tempname Directorio2

Si nuestro sistema no es *case sensitive*, puede ocurrir que queramos tener dos ficheros que se llaman igual, pero uno emplea mayúsculas y otro minúsculas, y git no nos lo deje incluir.

Por ejemplo, si tenemos `TFM.html` y `tfm.html` en local, y añadimos a git uno de ellos, luego no podremos añadir el otro a no ser que configuremos nuestro git como *case sensitive*:

    git config core.ignorecase false

Ahora ya podremos hacer `git add` con éxito.

La solución viene de [Stackoverflow](http://stackoverflow.com/questions/17683458/how-do-i-commit-case-sensitive-only-filename-changes-in-git)

### Borrar del repositorio<a id="orgheadline25"></a>

Borrar un archivo del repositorio sin borrarlo del sistema de directorios local:

    git rm --cached archivo.org

### Borrar un directorio<a id="orgheadline26"></a>

Para borrar un directorio:

    git rm --cached -r directorio

# Actualizar repositorio<a id="orgheadline28"></a>

Si queremos actualizar el repositorio con los cambios que se hayan producido en él, lo haremos con la opción `pull`:

    git pull

# Pull request<a id="orgheadline29"></a>

Haremos un *pull request* cuando queramos contribuir con nuestros cambios -mejoras, corrección de errores, actualizaciones- a un repositorio que ya existe.

Por eso, lo primero que tenemos que hacer es crear una copia del proyecto:

    git clone ruta-proyecto.git

Luego creamos una rama donde hacer las modificaciones:

    git checkout -b nueva-rama

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

# Borrar rama<a id="orgheadline30"></a>

En local:

    git branch -d rama-local

Si no se borra así, con `-D`

    git branch -d rama-local

En remoto::

    git push origin --delete rama-remota

o también:

    git push origin :ramaremota

# Mantener un repositorio forkeado actualizado<a id="orgheadline31"></a>

Añades upstream como servidor remoto:

    git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git

Actualizas upstream

    git fetch upstream

Actualizas el fork del repositorio original con sus cambios:

    git pull upstream master

# Publicación web<a id="orgheadline34"></a>

Si el contenido del proyecto es HTML, podemos utilizar a GitHub como servidor web de nuestro contenido web, a través de la funcionalidad [Pages](http://pages.github.com/).

Se puede hacer de dos maneras:

## Nombre del repositorio<a id="orgheadline32"></a>

Si el nombre del repositorio sigue la estructura "nombre-de-usuarix.github.io", el proyecto que cuelgue de ahí se publicará automágicamente en <http://nombre-de-usuarix.github.io>

## Rama gh-pages<a id="orgheadline33"></a>

Cualquier repositorio que tenga la rama `gh-pages` será publicado, y se verá su contenido web.

Por ejemplo, si tenemos un repositorio con nombre `mi-proyecto` que contiene una web y queremos publicarlo como página web, solo tenemos que crear una nueva rama `branch` de nuestro proyecto que llamaremos `gh-pages`:

    git checkout -b gh-pages

Luego ponemos ahí todo el contenido de la rama `master`:

    git merge master

Por último subimos a GitHub todo lo que tenemos en la nueva rama:

    $ git push -u origin gh-pages

En unos minutos, GitHub lo habrá publicado en una URL del tipo <http://nombre-de-usuarix.github.io/mi-proyecto>

Si tu repositorio es solo una web, puedes optar por utilizar solo la rama `gh-pages` en vez de mantener las dos ramas. Para ello tienes que elegir en GitHub qué rama utilizas.

Si mantienes las dos, actualizar la web se puede convertir en algo tedioso si lo haces habitualmente.

Para facilitar la tarea, [brettterpstra.com recomienda una solución](http://brettterpstra.com/2012/09/26/github-tip-easily-sync-your-master-to-github-pages/), puedes editar `.git/config` y añadir estas líneas a `[remote "origin"]`:

    push = +refs/heads/master:refs/heads/gh-pages
    push = +refs/heads/master:refs/heads/master

Quedando así:

    [remote "origin"]
            fetch = +refs/heads/*:refs/remotes/origin/*
            url = git@github.com:user/repo.git
            push = +refs/heads/master:refs/heads/gh-pages
            push = +refs/heads/master:refs/heads/master

De esta manera, cuando hagas git push lo harás en los dos repos.

# Problemas<a id="orgheadline37"></a>

## 403 fatal: HTTP request failed<a id="orgheadline35"></a>

<http://stackoverflow.com/questions/7438313/pushing-to-git-returning-error-code-403-fatal-http-request-failed>

    git remote set-url origin https://yourusername@github.com/user/repo.git

## git: error: src refspec master does not match any<a id="orgheadline36"></a>

<http://stackoverflow.com/questions/10568641/git-error-src-refspec-master-does-not-match-any>

    git remote rm origin
    git remote set-url origin git@....
    git push -u origin master

# Bibliografía<a id="orgheadline38"></a>

Algunos recursos:

-   [Git, distributed is the new centralized](https://git-scm.com/book/es)
-   <http://alistapart.com/article/get-started-with-git>
-   <http://progit.org/book/ch1-4.html>
-   [Qué es y cómo publicar nuestros proyectos en Github](http://ferblape.github.io/github.com-medialab-desigualdad)