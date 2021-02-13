# Ciencia-Datos-Python

Hoja de Trabajo No.1: Jypiter Notebooks, Markdown y Git
============================================================================================

Elaborada por: Margerys Salgado

# Ensayo acerca de GIT

## Introduccion
Existe distintos sistemas de control de versiones (VCS, por sus siglas en ingles), los mismos son aplicaciones que ayudan al programador durante el proceso de desarrollo del software. 
Lo interesante de estos VCS es que permiten a otros desarrolladores trabajar en el mismo proyecto, sin ocasionar perdida de datos o bloqueo de archivos.

El presente ensayo pretende explicar las funcionalidades del VCS Git, siendo uno de los más populares en el mundo de la programación.

## Sistema Git
La importancia de Git radica en el manejo de los datos, como un conjunto de copias instantáneas (snapshots) de un sistema de archivos, administrando las distintas versiones,
a través de un repositorio, donde programadores podrán trabajar en el mismo proyecto a través de copias locales.

Git nace en 2005, como un proyecto fácil de usar, diseño sencillo, eficiente con grandes proyectos y rápido.

Git proporciona líneas de códigos de registro donde se pueden observar las distintas versiones del proyecto, las modificaciones realizadas, quien las realizo, que día y hora se realizaron. 

Asimismo, a través de las bondades que presenta este sistema, el programador podrá aceptar los cambios realizados o continuar con versiones anteriores.

##### Descarga de Git:
Git es un sistema muy fácil de instalar, se puede obtener para los sistemas Linux, Mac y Windows, a través de este vínculo: https://git-scm.com/download. 
Actualmente en el sitio Web se encuentra la versión más reciente de Git 2.30.0.

##### Revisión de Directorio:
A través de Pytho se puede trabajar en conjunto los proyecto Git. 
Los siguientes códigos nos ayudan a revisar los archivos que tenemos y redireccionar el lugar donde queremos guardar nuestro nuevo proyecto. 
Que para este ejercicio se procedió a crear una carpeta llamada "Trabajo-Git".

%pwd  
%cd Desktop  
%cd Trabajo-Git  
%ls

##### Algunos comandos basicos en Git, que necesitas conocer:  
git init : iniciar un repositorio en Git; comenzar a trabajar en el working directory; vaciar un repositorio o reiniciar uno existente.  
git help: obtener ayuda con los códigos Git.  
git status : muestra el estado de los archivos.  
git add : agrega un archivo del working directory al staging area.  
git commit : graba los cambios en el repositorio o confirmar cambios. Es importante conocer que cada commit tiene su propio Hash.  
git checkout : cargar un commit.  
git checkin : hacer un commit.  
git push : actualiza cambios remotas.  
git pull : obtener o integrar cambios de otros repositorios.  
git clone : clonar un repositorio dentro de un nuevo repositorio.  


## Inicio con GIT  

##### Crear un repositorio local  
%system git init

##### Revisar el contenido del repositorio  
%system git status

A continuación se ilustraran ejemplos sobre la funcionalidades de Git, la manera como trabaja dentro de nuestra computadora y al momento de cargarlo a un repositorio GitHub, 
como se aplican sus códigos y como esta compuesto Git:  

### Blob:
En Git un archivo Blob son unidades de almacenamiento básicas, almacena el contenido de los archivos.
Para nuestro ejercicio se crearon archivos a través de Git utilizando el comando $ echo "nombre del archivo":  

Ejemplos:  

%echo "hello world" > hello.txt  
%echo "another line" >> hello.txt  

##### realizar cambios en el repositorio  
Para esta tarea deberás utilizar el código $git add  

%system git add hello.txt

### Commit: 
Cuando realizas los cambios que deseas, $git commit confirma los cambios y los guarda en el repositorio local.
Por cada cambio que se realice, Git guarda una snapshots; asimismo, crea un árbol con dos blob.  

Git genera información sobre el cambio, detallando el día, hora y usuario, con su propio Hash. Además, en el repositorio de Git se encontrarán todas las versiones.

##### Ejercicio 1:  

%system git commit
[master (root-commit) 84148ca] Add hello.txt
1 file changed, 1 insertion(+)
create mode 100644 hello.txt  
 
### Hash:
Es importante conocer que Git genera un código de 40 caracteres, llamado "Hash".
Hash es un Código de referencia para blob, tree, commit por cada cambio que se realice en los entornos.  

Ejemplos:

% commit 84148ca794260be0113dc26a124e6711c3930a6  
% tree 68aba62e560c0ebc3396e8ae9335232cd93a3f60  

### Tree:
Representa directorios para blobs o más árboles. Puede contener otros directorios.  

Ejemplo:

%system git cat-file -p 84148ca794260be0113dc26a124e6711c3930a60  

### Branch (rama):
Cada commit puede crear diferentes ramas, pero esta rama solamente conoce a su precedente. Las branch creadas por cada commit Git las llama Master. 
El programador puede trabajar en cada rama independiente de la versión. HEAD marca donde estamos trabajando.  

Ejercicio 1:

##### Crear una rama
%system git checkout master
Previous HEAD position was 84148ca Add hello.txt
Switched to branch 'master'
%system git branch  
        cat  
        dog  
      * master  
 
##### Visualizacion de rama
%system git log --all --graph --decorate  
* commit 219a62e81168a17ca3eb5f90dfd5b4ef6807de44 (master)  
| Author: Margerys Salgado <salgado.margerys@gmail.com>  
| Date:   Sun Feb 7 16:45:28 2021 -0600  
|  
|     X  
|  
* commit 84148ca794260be0113dc26a124e6711c3930a60 (HEAD)  
    Author: Margerys Salgado <salgado.margerys@gmail.com>
    Date:   Sun Feb 7 16:23:25 2021 -0600  
      
      Add hello.txt  

##### Visualizacion de rama
%system git log --all --graph --decorate --oneline  
* 62e3fc4 (HEAD -> master) X  
*   6e937bd (origin/master) Merge branch 'dog'  
|\  
| * 3e7a964 (dog) Add dog functionality  
* | ed47131 (cat) Add cat functionality  
|/  
* 72f07be Add animal.py  
* 219a62e X  
* 84148ca Add hello.txt  
​

### Cambiar de branch:
Para esta actividad es necesario utilizar $git checkout. En Git el programador puede elegir la rama en que desea trabajar y la versión que desea.  

##### Ejercicio 1:

%system git checkout -b <84147ca>
%system git checkout 84148ca  
Note: switching to '84148ca'.  

##### Ejercicio 2:

%system git checkout master  
Previous HEAD position was 84148ca Add hello.txt  
Switched to branch 'master'   

### Revisión de cambios:
Git siendo un sistema bastante amigable y útil para los programadores, permite poder revisar dentro del directorio los cambios realizados por los distintos
programadores, conociendo la información al detalle y los cambios exactos que realizo, haciendo uso $ git diff "nombre del archivo o Hash".

##### Ejercicio 1: a través del archivo

%system git diff hello.txt  
diff --git a/hello.txt b/hello.txt  
index fdff486..d7301eb 100644  
--- a/hello.txt  
+++ b/hello.txt  
@@ -1,2 +1,3 @@  
hello world  
-another line  
+anotherl line  
+comentario  

##### Ejercicio 2: utilizando su Hash

%system git diff 84148ca hello.txt  
diff --git a/hello.txt b/hello.txt  
index 3b18e51..d7301eb 100644  
--- a/hello.txt  
+++ b/hello.txt  
@@ -1 +1,3 @@  
hello world  
+anotherl line  
+comentario  

### Cargar funciones en Git:
El sistema a través del Git Bash, permite trabajar con funciones para cualquier programa que queramos, solamente se deberá agregar las extensiones correspondientes al nombre del archivo, para que el sistema reconozca el programa.

##### Ejercicio 1: python animal.py

%system import sys
​
def default():
    print('Hello')
​
def main():
    default()
​
if __name__ == '__main__':
    main()

##### Ejercicio 2:

%system import sys
​
def cat():
    print('Meow!')
    
def default():
    print('Hello')
​
def main():
    if sys.argv[1] == 'cat':
        cat()
    else:
        default()
​
if __name__ == '__main__':
    main()

### Rebase (Move):
Este código mueve todos los commit de un punto a otro. Cada commit que no sea el primero siempre dependerá del commit anterior, llamando a este $git commit base.

### Merge:
Es una alternativa para el uso del Rebase. En lugar de mover una rama, crea una función que conecta ambas ramas.

Ejercicio:

%system git merge --continue  
[master 6e937bd] Merge branch 'dog'  

### Remote:
Este código ayuda a el programador guardar su proyecto en un repositorio central.

Existes diferentes repositorios de códigos en las plataformas Web (repositorio central), donde los desarrolladores pueden mantener los códigos de sus proyectos. 
Dentro de estos Open Source está la herramienta de GitHub, que provee accesos a herramientas para desarrolladores.

Es necesario para tener acceso a GitHub (https://github.com/) contar con un usuario, que generar un espacio de trabajo donde otros programadores podrán ver los proyectos que realizas.

### log:
Despliega todos los commit realizados.

##### Ejemplo No.1
%system git log
commit 219a62e81168a17ca3eb5f90dfd5b4ef6807de44 (HEAD -> master)
Author: Margerys Salgado <salgado.margerys@gmail.com>
Date:   Sun Feb 7 16:45:28 2021 -0600
​
    X
​
commit 84148ca794260be0113dc26a124e6711c3930a60
Author: Margerys Salgado <salgado.margerys@gmail.com>
Date:   Sun Feb 7 16:23:25 2021 -0600
​
    Add hello.txt
log --all --graph --decorate: despliega con más detalles los commit realizados.


##### Ejemplo No.2
%system git log --all --graph --decorate --oneline  
* 62e3fc4 (HEAD -> master) X  
*   6e937bd (origin/master) Merge branch 'dog'  
|\  
| * 3e7a964 (dog) Add dog functionality  
* | ed47131 (cat) Add cat functionality  
|/  
* 72f07be Add animal.py  
* 219a62e X  
* 84148ca Add hello.txt 

### Pull:
Descarga los cambios. $git pull, trae los archivos nuevos creados en GitHub.

### Push:
Se utiliza en el proceso de cargar los cambios al repositorio remoto.

%system git push origin master:master  
Enumerating objects: 18, done.  
Counting objects: 100% (18/18), done.  
Delta compression using up to 12 threads  
Compressing objects: 100% (14/14), done.  
Writing objects: 100% (18/18), 1.69 KiB | 576.00 KiB/s, done.  
Total 18 (delta 3), reused 0 (delta 0), pack-reused 0  
remote: Resolving deltas: 100% (3/3), done.  
To https://github.com/ms0827/Ciencia-Datos-Python.git  
* [new branch]      master -> master  
​

### Clone:
Copia un repositorio.

%system git clone <URL o PATH del repositorio remoto>

### Fork:
Clona el repositorio en su cuenta de GitHub, en lugar de la computadora.

### GitHub
Es una plataforma Web que se utiliza como repositorios centrales para desarrolladores de proyectos utilizando el VCS de manera gratuita. 
Permite trabajar en colaboración con otras personas de todo el mundo, planificar proyectos y realizar un seguimiento del trabajo.

No se debe confundir los conceptos de Git y GitHub, el primero es un software de códigos abiertos, mientras que, GitHub es una plataforma de códigos abiertos, 
donde pueden trabajar desarrolladores de manera simultánea en un mismo proyecto de manera gratuita.

### Conclusiones  

Siendo Git un VCS, resulta muy útil para los programadores, ya que proporciona un espacio donde se pueden almacenar códigos de un proyecto particular, 
almacenando cada avance del mismo, sin lograr perder datos.

Git a través de GitHub proporciona un repositorio central, para trabajos en conjunto con varios desarrolladores.

Git proporciona herramientas útiles para dar seguimiento a cambios o nuevas actualizaciones, las cuales dependerá del objetivo del proyecto para aceptar los mismo.

Git contiene toda la historia de un proyecto en un mismo lugar y a través de su código Hash se puede tener un registro de todos los commit realizados.

Una de las cualidades más importantes de Git y GitHub son que las herramientas son softwares libres, fáciles de instalar y entender por usuarios que comienzan a incursionar 
en mundo de la programación.

