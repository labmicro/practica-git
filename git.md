# Guia Teórico Práctica de GIT

## Primera actividad práctica:

Creación del repositorio y explicación del contenido de las carpetas `.git` y de las áreas de trabajo y de preparación.

1.  Configura los valores globales de nombre y correo electrónico

    ```Bash
    git config --global user.name "You Name"
    git config --global user.email "youremail@yourdomain.com"
    git config --list
    ```

1.  Crear una carpeta `ejemplo` que contenga un archivo `archivo.md` con el siguiente contenido:

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT
    ```

1. Mostrar el contenido de la carpeta con el comando

    ```Bash
    tree -a -c
    ```

1. Crear un repositorio con el comando 

    ```Bash
    git init
    ```

1. Volver a mostrar el contenido de la carpeta con el comando

    ```Bash
    rm -r .git/hooks/*.sample
    tree -a -C
    ```

1. Mostrar el estado de los archivos del repositorio

    ```Bash
    git status
    ```

1. Agregar el archivo `archivo.md` al área de preparación con el comando

    ```Bash
    git add archivo.md
    ```

1. Mostrar el estado de los archivos del repositorio

    ```Bash
    git status
    ```

1. Mostrar el contenido de la carpeta con el comando

    ```Bash
    tree -a -C
    ```

1. Mostrar el contenido del archivo del área de preparación con el comando

    ```Bash
    git cat-file -p 229214f0deffcc96d55b69f2882b5c51d2bb5262
    ```

1. Cambiar el contenido del archivo `archivo.md` para que quede de la siguiente forma

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT

    Esta es la primera version muestra un ejemplo de un repositorio Git.
    ```

1. Mostrar el estado de los archivos del repositorio

    ```Bash
    # Se obtiene el estado de cada archivo del area de trabajo
    git status

    #Se obtienen los cambios del archivo respecto a la versión preparada
    git diff archivo.md
    ```

1. Actualizar el área de preparación para incluir los nuevos cambios

    ```Bash
    # Se guarda una copia del archivo actual en el area de preparación
    git add archivo.md
    ```

1. Mostrar el contenido de la carpeta con el comando

    ```Bash
    # Se puede observar los cambios en la carpeta .git/objects
    tree -a -C
    ```

1. Mostrar el contenido del archivo nuevo y del viejo en el área de preparación con el comando

    ```Bash
    # Se obtiene el contenido de la nueva versión del archivo
    git cat-file -p 1234c928ec1753d7ffcd79b758af90ab55e37de7
    
    # Se obtiene el contenido de la versión anterior del archivo
    git cat-file -p 229214f0deffcc96d55b69f2882b5c51d2bb5262
    ```

1. Compactar el repositorio y mostrar el contenido

    ```Bash
    # Se limpian los objetos sin vinculaciones
    git prune

    # Solo queda la versión actual del archivo en el area de preraración
    tree -a -C
    ```


## Segunda actividad práctica

Creación de dos commits, dos ramas y cambio de ramas. Explicación de la estructura del commit, de las etiquetas, de las ramas y del registro de cambios.

1. Confirmar los cambios preparados con el comando

    ```Bash
    git commit -m "Primera versión del ejemplo"
    tree -a -C
    ```

1. Explicar la información que se obtiene como resultado al hacer el commit

    ```Bash
    [master (root-commit) 5f6a407] Primera versión del ejemplo
    1 file changed, 3 insertions(+)
    create mode 100644 archivo.md
    ```
1. Mostrar el contenido y el contenido del commit, del árbol de directorios y del archivo almacenados con los comandos

    ```Bash
    git status
    tree -a -C

    # Se muestra la estiqueta master apuntando al commit
    cat .git/refs/heads/master

    # Se muestra el contenido del commit en si mismo
    git cat-file -p 5f6a407f4afd64e7f688c3c9f6c3b362155d34e8

    # Se muestra la lista de archivos almacenada en el commit
    git cat-file -p a9f20d16386352074a52612f3db7f21d15de518d

    # Se muestra el contenido de la version almacenda en el commit
    git cat-file -p 1234c928ec1753d7ffcd79b758af90ab55e37de7
    ```

1. Cambiar el contenido del archivo `archivo.md` para que quede de la siguiente forma

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT

    Este archivo muestra un ejemplo del uso de un repositorio Git.

    Ahora agregamos una nueva linea en el archivo para ver los cambios.
    ```    

1. Mostrar y almacenar los cambios en el repositorio con los comandos

    ```Bash
    # Se muestra el estado de los archivos en el area de trabajo
    git status

    # Se muestran los cambios respecto a la versión del ultimo commit
    git --no-pager diff

    # Se almacena la versión actual en el area de preparación
    git add archivo.md

    # Se muestra el estado de los archivos en el area de trabajo
    git status

    # Se confirman las versiones almacenadas en el area de preparación
    git commit -m "Segunda versión del ejemplo"

    # Se muestra el historial de cambios con todos los detalles
    git --no-pager log --graph

    # Se muestra el historial de cambios en una versión condensada
    git --no-pager log --graph --oneline
    ```

1. Mostrar el contenido del repositorio con los comandos

    ```Bash
    tree -a -C
    
    # Se obtiene el HASH del nuevo commit
    cat .git/refs/heads/master
    
    # Se muestra el contenido del commit en si mismo
    git cat-file -p da9520f00726cb2d1e8bab62e5eb5fd7abadf00b

    # Se muestra la lista de archivos almacenada en el commit
    git cat-file -p d026e384944f7f7fa0947fa524483bc3ffe4bad9

    # Se muestra el contenido de la version almacenda en el commit
    git cat-file -p 5f1d6fa6a1e438409155dceb5f5268b9f3c569ec
    ```

1. Crear una nueva rama `develop` y desplegarla con los comandos

    ```Bash
    # Se crea una nueva rama llamada develop
    git branch develop

    # Se muestra la rama develop apuntando al mismo lugar que la master
    git --no-pager log --graph

    # Se muestra que la rama seleccionada sigue siendo la rama master
    git status

    # Se cambia de la rama master a la rama develop
    git checkout develop

    # Se muestra que la rama seleccionada es ahora develop
    git status
    ```

1. Cambiar el contenido del archivo `archivo.md` para que quede de la siguiente forma

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT

    Esta es la primera version, muestra un ejemplo de un repositorio Git.

    Esta es la tercera versión, editamos la linea para ver cambios.
    ```    

1. Inspeccionar y confirmar los cambios en el repositorio con los siguientes comandos

    ```Bash
    # Se muestra el estado de los archivos en el area de trabajo
    git status

    # Se muestran los cambios respecto a la versión del ultimo commit
    git --no-pager diff

    # Se almacena la versión actual en el area de preparación
    git add archivo.md

    # Se muestra el estado de los archivos en el area de trabajo
    git status

    # Se confirman las versiones almacenadas en el area de preparación
    git commit -m "Tercera versión del ejemplo"

    # Se muestra el historial de cambios con todos los detalles
    git --no-pager log --graph
    ```

1. Mostrar el contenido del repositorio con los comandos

    ```Bash
    # Ahora hay dos archivos en la carpeta .git/refs/heads
    tree -a -C
    
    # La rama develop apunta al nuevo commit
    cat .git/refs/heads/develop
    
    # Se muestra el contenido del commit apuntado por develop
    git cat-file -p 4284944d4645b33761bd42d7e14bee5996be1038

    # La rama master apunta a otro commit, el padre del nuevo commit
    cat .git/refs/heads/master

    # Se muestra el historial de cambios de la rama develop
    cat .git/logs/refs/heads/develop

    # Se muestra el historial de cambios de la rama master
    cat .git/logs/refs/heads/master

    # Se muestra el historial de cambios del repositorio
    cat .git/logs/HEAD
    ```

1. Cambiar de rama y mostrar la diferencia de contenido del archivo

    ```Bash
    # Se muestra el contenido del archivo de la rama develop
    cat archivo.md

    # Se cambia la copia de trabajo a la rama master
    git checkout master

    # Se muestra el contenido del archivo de la rama master
    cat archivo.md
    ```

1. Cambiar el contenido del archivo `archivo.md` para que quede de la siguiente forma

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT

    Esta es la primera version, muestra un ejemplo de un repositorio Git.

    Esta es la segunda versión, editamos la linea para ver cambios.

    Esta es una nueva versión, se agrega otra linea mas al final.

    Esta es una linea que se va a perder.
    ```

1. Intentar cambiar de rama con el archivo editado para mostrar el error con los siguientes comandos

    ```Bash
    # Se muestra el estado de la copia de trabajo
    git status

    # Se muestra el error al tratar de sobreescribir un archivo editado
    git checkout develop

    # Se muestra el contenido del archvio
    cat archivo.md

    # Se fuerza la actualizción de la copia de trabajo a la rama master
    git checkout -f develop

    # Se muestra el contenido del archvio
    cat archivo.md
    ```

## Tercera actividad práctica

Mezcla y reorganización de ramas sin conflictos


1. Crear el archivo `nuevo.md` con el siguiente contenido

    ```Markdown
    # Este es un nuevo archivo que se suma al proyecto

    Esta es la primera version del nuevo archivo.
    ```

1. Confirmar los cambios en la rama master y mostrar el gráfico de historia de las ramas con los siguientes comandos

    ```Bash
    # Se vuelve a desplegar la rama master
    git checkout master

    # Se almacena la versión actual en el area de preparación
    git add nuevo.md

    # Se muestra el estado de los archivos en el area de trabajo
    git status

    # Se confirman las versiones almacenadas en el area de preparación
    git commit -m "Cuarta versión del ejemplo"

    # Se muestra el historial de la rama actual
    git --no-pager log --graph

    # Se muestra el historial completo del repositorio en una linea
    git --no-pager log --all --graph --oneline
    ```

1. Copiar el repositorio en el estado actual y mostrar el procedimiento de mezcla sin conflictos con los siguientes comandos

    ```Bash
    # Se crea un clon del repositorio en la carpeta copia
    cp -R . ../mezcla

    # Cambiar a la carpeta copia para trabajar con el clon del repositorio
    cd ../mezcla

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph

    # Se mezcla la rama develop en la rama master
    git merge develop

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph
    ```

1. Copiar el repositorio original en el estado actual y mostrar el procedimiento de reorganización sin conflictos con los siguientes comandos

    ```Bash
    # Cambiar a la carpeta del repositorio original
    cd ../ejemplo

    # Se crea un clon del repositorio en la carpeta copia
    cp -R . ../rebase

    # Cambiar a la carpeta copia para trabajar con el clon del repositorio
    cd ../rebase

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph

    # Se despliega la develop
    git checkout develop

    # Se reorganiza a partir de la rama master
    git rebase master

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph
    ```        

1. Mezclar la rama master con la develop para unificar las versiones.
    
    ```Bash
    # Se despliega la master
    git checkout master
    
    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph

    # Se mezcla la rama master con la develos utilizando avance rapido
    git merge --ff develop

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph


## Cuarta actividad práctica

Mezcla y reorganización de ramas con conflictos

1. Cambiar el contenido del archivo `archivo.md` para que quede de la siguiente forma

    ```Markdown
    # Seguimiento de Cambios en Repositorios GIT

    Esta es la primera version, muestra un ejemplo de un repositorio Git.

    Esta es la segunda versión, agregamos una linea para ver cambios.

    Esta es una nueva versión, se agrega otra linea mas al final.
    ```

1. Copiar el repositorio en el estado actual y mostrar el procedimiento de mezcla con conflictos con los siguientes comandos

    ```Bash
    # Se crea un clon del repositorio en la carpeta copia
    cp -R . ../mezcla

    # Cambiar a la carpeta copia para trabajar con el clon del repositorio
    cd ../mezcla

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph

    # Se mezcla la rama develop en la rama master
    git merge develop

    # Se resuelve el conflicto editando el archivo
    nano archivo.md

    # Se almacena la versión actual en el area de preparación
    git add archivo.md

    # Se muestran los cambios efectivos a confirmar
    git --no-pager diff --staged

    # Se confirman las versiones almacenadas en el area de preparación
    git commit -m "Quinta versión del ejemplo"

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph
    ```
1. Copiar el repositorio original en el estado actual y mostrar el procedimiento de reorganización con los siguientes comandos

    ```Bash
    # Cambiar a la carpeta del repositorio original
    cd ../ejemplo

    # Se crea un clon del repositorio en la carpeta copia
    cp -R . ../rebase

    # Cambiar a la carpeta copia para trabajar con el clon del repositorio
    cd ../rebase

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph

    # Se despliega la develop
    git checkout develop

    # Se reorganiza a partir de la rama master
    git rebase master

    # Se resuelve el conflicto editando el archivo
    nano archivo.md

    # Se almacena la versión actual en el area de preparación
    git add archivo.md

    # Se muestran los cambios efectivos a confirmar
    git --no-pager diff --staged

    # Se confirman las versiones almacenadas en el area de preparación
    git rebase --continue

    # Se muestra el historial completo del repositorio
    git --no-pager log --all --graph
    ```        

## Quinta actividad práctica

Uso de repositorios remotos

1. Crear una clave SSH con los siguientes comandos

    ```Bash
    # Generar una nueva clave SSH, dejando todas las opciones por defecto
    ssh-keygen

    # Obtener la parte publica de la clave y copiarla en el portapapeles
    cat ~/.ssh/id_rsa.pub
    ```

1. Crear una cuenta, dar de alta la clave SSH y crear un repositorio

    1. Abrir la página de GitHub y hacer clic en el botón de *Sing Up*.
    1. Ingresar a GitHub haciendo clic en *Sing In* y completado el correo electrónico y la clave.
    1. Ingresar a la configuración haciendo clic en la foto del perfil arriba a la derecha y seleccionando la opción *Seetings* del menú.
    1. Seleccionar la opción *SSH and GPG keys* del menú lateral.
    1. Hacer clic en el botón *New SSH key*.
    1. Completar el título con un nombre que permita reconocer la clave en caso de necesitar borrarla, el nombre de usuario @ el nombre de la máquina utilizada es una buena alternativa.
    1. Pegar la clave pública copiada en el paso anterior y agregarla con el botón *Add SSH key*.
    1. Crear un nuevo repositorio haciendo en el botón *+* arriba a la derecha y seleccionando la opción *New repository* en el menú.
    1. Definir el nombre del repositorio como *ejemplo*. **No se debe tildar la opción de generar un README y las plantillas para el archivo .gitignore ni para la licencia deben permanecer en None**. Completar la operación haciendo clic en el boton *Create repository*
    1. Obtener la URL del repositorio haciendo clic en la opción SSH.

1. Enviar los cambios al servidor con los siguientes comandos

    ```Bash
    # Se define un remoto con el nombre origin y la url obtenida del paso anterior
    git remote add origin git@github.com:evolentini/ejemplo.git

    # Se envia la rama master al servidor de destino
    git push -u origin master
    ```

1. Mostrar que en el servidor de GitHub solo existe la rama master

1. Enviar los cambios en todas las ramas al servidor con los siguientes comandos

    ```Bash
    # Se envian todas las ramas al remoto
    git push --all
    ```

1. Clonar el repositorio en una carpeta independiente

    ```Bash
    # Se clona el repositirio en una carpeta hermana
    git clone git@github.com:evolentini/ejemplo.git ../clonado

    # Se cambia a la nueva copia del repositorio
    cd ../clonado

    # Se muestra el historial completo del repositorio clonado
    git --no-pager log --all --graph

    # Se muestra la diferencia en los objetos Git compactados
    tree -a -C
    ```

