
AREAS TRABAJO EN GIT
Se refiere al estado en el que puede estar un archivo en git dentro del proceso
de "llevar" ese archivo al repositorio. Son 3 áreas:

1. Directorio de trabajo (Working directory): carpeta del proyecto que contiene
  los archivos, carpetas y el directorio .git del repositorio. Estos componentes
  NO son parte del repositorio y NO se han añadido al área de preparación
  Cuando un archivo se encuentra en esta área decimos que se encuentra en una
  verisón MODIFICADA (MODIFIED).

-> para pasar a la siguiente área usar el comando add

2. Área de preparación (Stage / Staging area): es el área intermedia en la que
   se preparan los archivos y cambios que se van a subir al repositorio, es 
   decir, serán incluídos en el próximo commit. Tener en cuenta que ésta no es
   una área definitiva, aún aquí se pueden agregar o eliminar componentes del 
   futuro commit. Estos componentes NO son parte del repositorio.
   Cuando un archivo se encuentra en esta área decimos que se encuentra en una
   versión PREPARADA (ON STAGE). 

-> para pasar a la siguiente área usar el comando commit

3. Repositorio (directorio .git): área final (repositorio) donde se encuentran
   los archivos. Es la parte que se copia cuando clonas un repositorio a tu
   computadora.
   El directorio .git contiene los metadatos, ramas y versiones del proyecto 
   que se han ido subiendo.
   Cuando un archivo se encuentra en esta área decimos que se encuentra en una
   verisón CONFIRMADA (COMMITTED).

# ¿QUÉ ES UN COMMIT?

Es un componente básico de la línea del tiempo de un proyecto de Git. Es un 
registro como una foto del estado de un proyecto en un momento especifico. Un
commit registra los cambios al detalle en los arhivos en comparación con la
versión anterior, si se modificaron, si se agregaron o quitaron, si se cambió
el nombre, si se crearon, modificaron o eliminaron carpetas, etc. Todos los
cambios entre un commit y otro van a estar registrados en el siguiente commit.
La idea es que con los commits podamos rastrear los cambios en los proyectos,
cuando se necesite incorporar una nueva versión, agragar funcionalidades, 
solucionar problemas o incluso regresar a una versión anterior u otras
necesidades que marquen un cambio en los archivos del proyecto, se crea un
commit.

ESTRUCTURA DE UN COMMIT
Git crea un identificador SHA (Secure Hash Algorithm) único también llamda
"hash" para cada commit con el que podremos referirnos a él para ciertas
operacines muy útiles. El SHA identifica los cambios realizados, dónde se
realizaron los cambios y quién realizó los cambios.
Con cada commit, Git también asocia una fecha automática del momento en que se
crea el commit.
Cada vez que se crea un commit se debe especificar un usuario, un correo, una
descripción. El usuario y el correo normalmente ya estarán definidos con
anterioridad, pero la descripción se tiene que incluir con cada commit. Esta
descripción es muy imporante ya que explica de forma concisa el motivo del
commit, de manera entendible para otros usuarios o para uno mismo en el futuro.

Para crear un commit en git hay que hacerlo con el comnado commit. Ya debe
haberse creado un repositorio con el comando init y tener archivos en el área
de prepación generados con el comando add.

# ¿Qué es una rama (branch)?
Es una línea independiente de desarrollo en el repositorio, que evolucionará
paralelamente a la rama principal y que puede o no volver a unirse a ella, 
pudiendo tener versiones diferentes del mismo proyecto.
Para crear una rama o ver las que actualmente existen en el repositorio actual
usar el comando branch.
Para cambiar de rama actual usar el comando checkout.
Para fusionar ramas usar el comando merge.







-------------------------------------------------------------------------------
*******************************************************************************
-------------------------------------------------------------------------------

COMANDOS GIT
se debe escribir git antes de cada comando

config
    para la configuración de git.

    --global
        para que las configuraciones que se hagan afecten a todo git. Se se
        omite, las configuraciones afectarán sólo al repositorio actual.

    user.name "nombre"
        para configurar el nombre del ususario de git. Normalmebte debría
        ser el nombre del ususario de la cuenta de github ya que este
        nombre es el que aparecerá en los commits que este usuario suba.
        Si no se especifica el argumento nombre, devuelve el nombre actual.
        configurado.

    user.email "correo"
        para configurar el correo del usuario de git. Normalmente debería
        ser el correo del usuario de la cuenta de github ya que este
        correo es el que aparecerá en los commits que este usuario suba.
        Si no se especifica el argumento correo, devuelve el correo actual.
    
    core.editor
        para asociar un editor (IDE) con Git.
        Ejemplo. Asociar Visual Studio Code con Git:
        git config --global core.editor "code --wait"
        --wait le dice a Git que espere hasta que el archivo se guarde, y se
        cierre para culminar con el commit



init
    (Initialize) Inicializa un repositorio git vacío ¿local? en la carpeta
    actual. Crea la carpeta .git en la que se encuentra toda la info del
    repositorio. Si se borra esta carpeta el respositorio no existirá.

    .defaultBranch "nombre"
        cambia la denominación (no el nombre) de un repositorio o de todos los
        repositorios futuros, se decir, el nombre por defecto.
        Ejemplo. para cambiar la denominación por defecto de los respositorios
        futuros a "main":
        git config --global init.defaultBranch main

status
    Para verificar el estado del repositorio. Muestra la rama actual, los 
    commits realizados, los componentes en el área de preparación etc.
    Tener en cuenta que este comando sólo nos muestra info de los repositorios
    locales. Si se actualiza un repositorio remoto, status no nos podrá decir
    si nuestros repositorio local está actualizado. Si se desea verificar el
    estado de nuestro repositorio local respecto al remoto utilizar el comando
    fetch y si se desea descargar y combinar lo que hay remoto con lo que hay 
    en local utilizar el comando pull

add
    para agregar archivos desde el directorio de trabajo hacia el área de
    preparación. 
    Ejemplo. Para agregar el archivo mi-archivo.txt al área de preparación:
    git add mi-archivo.txt
    Se puede obviar escribir el nombre de los archivos escribiendo un punto
    en lugar de los archivos. 
    Ejemplo. Agregar los arhchivos modificados cualesquiera q sean al stage:
    git add .

rm
    --cached
            para eliminar archivos del área de preparación. Estos archivos
            regresarán a ser parte del directorio de trabajo. 
            Ejemplo. para remover el archivo mi-archivo.txt del área de preparación:
            git rm --cached mi-archivo.txt

commit
    Sube los cambios del área de preparación al repositorio. Ya debe haberse
    creado un repositorio con el comando init y tener archivos en el área de
    prepación generados con el comando add. Se puede incluir una descripción
    con el flag -m.
    Ejemplo. Crea un commit con la descripción de que se está agregando el 
    archivo mi-archivo.txt:
    git commit -m "Agregar archivo: mi-archivo.txt"
    Lo ideal es trabajar en conjunto con visual studio code para trabajar la
    descripción de manera más interactiva y no con el flag -m. Para hacer esto
    sólo hay que ejecutar este comando sin argumentos ni flags:
    git commit y enter, esto hará que se abra VS Code con un archivo y
    esperará a que se guarde y se cierre para terminar con el commit.
    Para crear commits dentro de una rama sólo hay que estar en ella.
    
    --amend
        para modificar un commit. Hay que tener mucho cuidado con editar commits
        ya que ya podría haber sido descargado por otro usuario antes de hacer
        la modificación. Lo recomendable es hacer estas modificaciones en local.
        --amend espera a que se cierre el archivo de mensaje (en le editor) para
        terminar con la edición del commit.

    -m 
        para indicar el mensaje del commit. Tiene que ser sí o sí una única
        línea.

log
    Muestra el historial de commits realizados con su respectiva información
    descriptiva (SHA, rama, autor, correo, fecha, descripción)

    --oneline
        para mostrar el historial de commits cada uno en una linea.

    -p
        para ver las diferencias entre los commits. no entiendo bien los mensajes en este modo !!!!!!!!!!!
    
reset
    para dehacer un commit (eliminarlo). 
    Ejemplo. Para eliminar el último commit:
    git reset --soft HEAD~1
    --soft : los archivos en el directorio de trabajo nose ven afectado por la
    eliminación del commit, quedan tal cual están antes de eliminar el commit,
    quedarían en el working area. En Visual Studio quedarían marcados con la 
    letra M en señal de que están modificados, ya que esa es su situación real
    ahora, el commit que los actualizó en el repositorio ya no existe por tanto
    son cambios pendientes de agregar al stage y luego al repositorio como si
    fueran archivos que nunca se subieron.
    HEAD~1 : deshace un cambio desde el HEAD (desde lo último commit subido)

branch
    Para crear ramas nuevas en el repositorio o ver las que actualmente existen,
    borrar ramas.
    Ejemplo. Crear una rama con el nombre version-JavaScript:
    git branch version-JavaScript
    Ejemplo. Para ver (listar) las rammas que actualmente existe:
    git branch
    La rama en la que se está trabajando (actual) tiene un * al inicio
    
    -m
        para cambiar el nombre de una rama. hay 2 formas de cambiar el nombre a
        una rama:
        1° Indicando sólo el nuevo nombre. De esta forma necesario que la rama
        a la que se desea cambiar nombre sea la rama actual.
        Ejemplo. Cambiar de nombre a la rama actual a "version-js":
        git branch -m version-js
        2° Indicando el nombre antiguo y el nuevo nombre de la rama a cambiar.
        De esta forma no es necesario estar en la rama a la que renombrar.
        Ejemplo. Cambiar el nombre de la rama "version-JavaScript" a "version-js":
        git branch -m version-JavaScript version-js

    -d
        Para borrar una rama. Esto aplica para repositorios locales, no en las
        ramas que ya están publicadas en Github. Si la eliminación fue exitosa,
        Git muestra un mensaje confirmando la eliminación de la rama.
        La rama main (o principal) no se puede eliminar, tampoco se puede borrar
        la rama actual, se debe borrar desde otra rama.
        Ejemplo. Borrar la rama "version-py":
        git branch -d version-py


checkout
    para cambiar de rama actual o para crear una nueva rama y cambiar a esa
    rama como actual. Cuando se ejecuta este comando, Git muestra el mensaje:
    Switched to branch ... indicando el cambio a la rama indicada.
    Ejemplo. Cambiar a la rama version-JavaScript:
    git checkout version-JavaScript
    
    -b 
        crea una rama nueva rama nueva.
        Ejemplo. Crear y cambiar a una rama llamada version-Python
        git checkout -b version-Python
    
    origin/main
        Cambia al repositorio REMOTO origin y a su rama main pero para trabajar
        de manera local. En este caso se muestra un msg que se puede hacer 
        cambios en local que no van a modificar la información en el remoto. Es
        muy útil ya que si se trabaja con VS Code, se puede ver los archivos en
        local con los cambios realizado en el retomo
    
merge
    para fusionar ramas. Se debe estar en la rama que recibirá la fusión.
    Notar que mientras se está haciendo la fusión, el mensaje de Git sobre la
    rama actual muestra también la palabra MERGING: (main|MERGING)
    Ejemplo. Fusionar la rama "version-js" con la rama actual:
    git merge version-js

    --continue
        Cuando una fusión de ramas tiene conflictos, primero hay que solucionar
        esos conflictos y luego continuar el proceso de fusión con este comando.
        Cuamdo se ejecuta este comando los conflictos deben estar solucionados
        ya que serán subidos al repositorio como un nuevo commit, en VS Code se
        abre una pestaña nueva esperando confirmar el mensaje de descripción y
        cerrar el archivo para terminar con la fusión y el commit automático.
        Al terminar la fusión Git muestra un msg indicando lo correspondiente.
        En el siguiente texto se ha unido la rama 'version-js' a la rama main:
        HP@HPV MINGW64 ~/ruta-reposistorio (main|MERGING)
        $ git merge --continue
        [main 34fd113] Merge branch 'version-js'

clone   
    Crea una copia local de un repositorio remoto. Este repositorio estará 
    alojado en GitHub y ahí hay que obtener la dirección HTTPS de clonación del 
    repositorio para agregarla como argumento a este comando. Hay que tener en 
    cuenta que git crea el repositorio en la carpeta que actualmente se está 
    trabajando, por tanto ante de ejecutar este comando hay que asegurarse estar 
    en la carpeta adecuada. Git mostrará unos mensajes del proceso indicando que 
    el proceso ha sido realizado al 100%
    Ejemplo. Clonar el repositorio de GitHub 'nuevo-proyecto':
    git clone https://github.com/usuario/nuevo-proyecto.git
    En este caso la dirección htts ha sido obtenida del repositorio en la web 
    de GitHub.
    Pero ocurre algo al querer enviar los cambios de vuelta al repositorio 
    remoto, en este caso solo hemos hecho una copia en local. Si intentamos 
    hacer git push tendremos un error ya que no hemos definido ningún origen 
    remoto para este directorio. Para guardar en forma remota (usando GitHub) 
    debemos crear un repositorio, conectarlo a nuestra carpeta local con 
    'git remote add origin ruta' y de esa forma estaremos habilitados para guardar los 
    cambios en remoto.

remote
    Verifica el nombre que se le ha asignado al repositorio remoto en GitHub
    para trabajar con Git. Éste no es el nombre del repositorio real cuando se
    creó y no lo sustiruirá, es sólo un nombre temporal para trabajar con el
    repositorio local y remotamente a la vez. Normalmente casi siempre este 
    nombre será 'origin'

    -v
        muestra las direcciones del repositorio origen para push (enviar
        cambios) y fetch (visualizar cambios). Nommalmente serán la misma 
        dirección para ambos. Este comando no muestra ninguna info si no hay 
        respositorios conectados. Utilizar add para agregar repositorios 
        remotos antes de utilizar este comando.
    
    add
        visibiliza un repositorio remoto a gitbash para poder actualizar cambios.
        Este comando no crea commits ni sube archivos ni hace nada de ello, Lo
        único que hace es dar visibilidad a un repositorio remoto en gitbash,
        para ello hay que indicar la dirección o link del repositorio remoto.
        Después se puede utilizar -v
        Ejemplo. Agregar a un repositorio remoto (normalmnente origin):
        git remote add origin https://github.com/usuario/repositorio.git

push
    Envía los cambios realizados en un repositorio local a un repositorio remoto
    para que ambos tengan la misma información y estén sincronizados, creando
    una conexión entre el repositorio local y el remoto.
    ¿push hace un commit???
    Ejemplo. Enviar datos desde un repositorio local a la rama main de un
    repositorio remoto:
    git push origin main

pull
    Descarga el contenido de un repositorio remoto e inmediatamente actualiza
    un repositorio local para que ambos tengan la misma información si no hay
    conflictos. A diferencia del comando fetch, pull combina los cambios
    automáticamente.
    Si no hay cambios en el remoto, este comando no hace nada. No 
    es necesario luego usar otro comando como fetch. Lo que si puede ser
    necesario es utiliar el comando log para ver los nuevos commits traídos a
    local
    Ejemplo. Para actualizar un repositorio local desde uno remoto origni 
    (verificar este nombre con git remote -v) hacia nuestra rama main:
    git pull origin main

fetch
    Verifica si se han realizado cambios en el repositorio remoto desde la
    última vez que actualizaste tu respositorio local con git pull, sin 
    combinar esos cambios con el repositorio local y nos permite ver como una 
    vista previa de esos cambios y luego podemos elegir si queremos conbinarlos o no con el
    comando merge. Se diferencia del comando pull que sí combina los cambios.
    Ejemplo
    git fetch origin
-------------------------------------------------------------------------------
*******************************************************************************
-------------------------------------------------------------------------------

COMANDOS GENÉRICOS DE LA LÍNEA DE COMANDOS

cd
    para cambiar directorio. 
    Cuando sólo se escribe cd nos lleva al directorio raíz
cd .. 
    para subir un directorio
cd "ruta"
    para ir a la ruta especificada. Se debe especificar comillas cuando la ruta contiene espacios en blanco

clear
    limpia la pantalla

ls
    para listar archivos y carpetas dentro de la carpeta actual. Las carpetas se diferencian de los archivos por que terminan en /

mkdir
    Make dir. Para crear un directorio

rmdir
    Remove dir. Para eliminar directorios