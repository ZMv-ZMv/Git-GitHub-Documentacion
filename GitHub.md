# PROCESOS

## PARA CREAR UN REPOSITORIO LOCAL (VACÍO)

1.  Abrir la git bash
2.  Situarse en la carpeta deseada que luego contendrá la carpeta .git que 
    definirá la creación de un repositorio
3.  Usar el comando init:
    git init
4.  Listo. la carpeta .git debe haberse creado y se debe mostrar la ruta
    terminando en '(main)', lo que indica que se está en la rama main del 
    repositorio nuevo.

Tener en cuenta que este proceso NO crea un commit, hay que hacerlo con el
comando git commit, lo que será el primer commit del repositorio, a diferencia
de crear un repositorio nuevo desde GitHub que automáticamente te crea un 
commit cuando creas un repositorio nuevo.


## PARA CREAR UN REPOSITORIO LOCAL Y ENVIARLO LUEGO A REMOTO (GITHUB)
ENVIAR!!

1.  Tener o crear un repositorio local (con gitbash) que será el que se subirá.
    Este repositorio es el que tiene los archivos y commits que se desean subir.
2.  ¿Tener? o crear un nuevo repositorio remoto (en GitHub) que será el que 
    recibirá el repositorio local. No es necesario que éstos dos repositorios 
    tengan el mismo nombre.
3.  en gitbash ejecutar el comando remote con add y la ruta https del 
    repositorio remoto creado en el paso 2:
    git remote add origin https://github.com/usuario/repositorio.git
4.  Enviar la info del repositorio local al repositorio remoto con push (a la 
    rama main del origin):
    git push origin main
5.  Gitbash muestra un msg indicando que entre otras cosas, que se ha creado la
    rama main en el repositorio remoto nuevo creado en el paso 2. Además en
    VS Code también se empezarán a sincronizar los cambios.

## BIFURCAR (FORK) UN REPOSITORIO
Crear una copia del re