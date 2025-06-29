
# 🚀 Curso de Git y Terminal - Tecnicatura

Este curso está diseñado para introducirte al mundo de Git, GitHub y la terminal de comandos. A lo largo de las clases, aprenderás desde los comandos más básicos hasta técnicas más avanzadas de control de versiones y manejo de ramas con Gitflow.

---

## 📅 CLASE 1 - Introducción a la Terminal

### 📁 Navegación y Comandos Básicos

```bash
pwd             # Muestra la ruta actual
cd              # Cambia de directorio
cd /            # Ir a la raíz del disco
cd ~            # Ir a la carpeta del usuario
ls              # Lista los archivos del directorio actual
ls -al          # Lista todo, incluyendo archivos ocultos
clear           # Limpia la terminal
cd ..           # Sube un nivel
cd U + [Tab]    # Autocompletado
cd /D           # Cambia de disco (Windows)
df -h           # Muestra espacio en disco (Linux)
cd /mnt/d       # Accede al disco D desde WSL
```

### 🗂️ Creación de Carpetas

```bash
mkdir Tecnicatura
cd tecnicatura
mkdir Python Java JavaScript
```

---

## 📅 CLASE 2 - Primeros pasos con Git

### 📄 Archivos y Repositorio

```bash
touch vacio.txt     # Crea un archivo vacío
cat vacio.txt       # Muestra el contenido
history             # Historial de comandos
!72                 # Ejecuta el comando número 72
rm vacio.txt        # Borra archivo
```

### 🧱 Inicializar Git

```bash
git init
git config --global user.name "Ariel Betancud"
git config --global user.email "betancudariel@gmail.com"
git add .
git commit -m "Primer commit"
git log
```

---

## 📅 CLASE 3 - Archivos y README

```bash
mkdir class-git
cd class-git
touch README.md
git add .
git commit -m "Agregar README"
```

---

## 📅 CLASE 4 - Commits en profundidad

```bash
touch historia.txt
git add .
git commit
# En Vim:
Esc + :wq!
# o
Esc + Shift + Z + Z

git log historia.txt
git diff <hash_viejo> <hash_nuevo>
```

---

## 📅 CLASE 5 - Gitflow y ramas

### 🤓 ¿Qué es el staging?
Es el área donde Git guarda cambios antes de confirmarlos con un commit.

### 🌿 Gitflow: Modelo de ramas
- **Master**: rama principal
- **Develop**: rama de desarrollo
- **Feature**: para nuevas funciones
- **Release**: estabilizar código antes del despliegue
- **Hotfix**: para corregir errores críticos

```bash
git branch cambios
git checkout master
git branch second
git branch hotfix
git branch -d cambios  # Elimina rama
```

---

## 📅 CLASE 6 - Volver en el tiempo: `reset` y `checkout`

```bash
git log --oneline
git reset <hash> --soft   # Vuelve a commit anterior sin borrar cambios
git reset <hash> --hard   # Borra todo
git checkout <hash>       # Ver versión específica
git checkout master       # Vuelve a la rama principal
```

---

## 📅 CLASE 7 - `git reset` vs. `git rm`

### 🔁 `git reset`
- `--soft`: mantiene cambios en staging
- `--mixed`: saca de staging
- `--hard`: borra todo

### ❌ `git rm`
- `--cached`: saca del staging, conserva archivo
- `--force`: elimina completamente

```bash
git reset HEAD archivo    # Saca del staging
git rm --cached archivo   # Deja de trackear
```

---

## ✅ Conclusión

Este curso te da las herramientas esenciales para manejar proyectos con Git desde la línea de comandos. Aprende buenas prácticas, como trabajar con ramas, y conoce las diferencias entre `reset`, `rm`, y `revert`.

---




# 📚 CLASE 8 - COMANDOS PARA TRABAJO REMOTO EN GIT

---

## 🧩 Trabajo Remoto con GIT

### 🔄 Clonar, enviar y recibir cambios

```bash
git clone url_del_servidor_remoto
# Clona el repositorio remoto (rama principal + historial completo)

git push
# Envía tus commits al repositorio remoto (usualmente después de git add y git commit)

git fetch
# Descarga cambios desde el repositorio remoto sin aplicarlos aún

git merge
# Combina los cambios descargados (con fetch) con tu rama actual

git pull
# Hace un fetch + merge en un solo paso
📜 Visualizar Historial de Cambios
📌 Básico

git log --oneline
# Muestra el hash abreviado + mensaje de commit

git log --decorate
# Añade información de HEAD, ramas y etiquetas

git log --stat
# Muestra resumen de archivos modificados y líneas añadidas/borradas

git log -p
# Muestra los diffs completos entre commits

##CLASE 9A - RAMAS EN GIT 

---

## 🌿 ¿Cómo funcionan las ramas en GIT?

Las ramas son la manera de hacer cambios en nuestro proyecto sin afectar el flujo de trabajo de la rama principal.  
Esto es porque queremos trabajar una parte muy específica de la aplicación o simplemente experimentar. ✨

---

## 🧰 Comandos básicos para manejar ramas

```bash
🌱 git branch nombre-rama  
# Con este comando se genera una nueva rama.

🔄 git checkout nombre-rama  
# Con este comando puedes saltar de una rama a otra.

⚡ git checkout -b rama  
# Genera una rama y nos mueve a ella automáticamente, 
# es decir, es la combinación de git branch y git checkout al mismo tiempo.

⏪ git reset id-commit  
# Nos lleva a cualquier commit sin importar la rama, eliminando el historial posterior al commit seleccionado.

👀 git checkout rama-o-id-commit  
# Nos lleva a cualquier commit sin borrar commits posteriores.
🧪 Práctica: Crear y fusionar ramas
Mientras la rama master está cambiando normalmente, vamos a crear una rama paralela que agregará nuevas secciones.
Esta rama la llamaremos second (segunda).

Al crear otra rama, estamos haciendo una copia de todos los commits actuales de master.

Todos los cambios que hagamos en second no se verán en master hasta que hagamos un merge (fusión). 🔀

💻 Preparación del entorno
Ubuntu:

# Abrir terminal
cd Tecnicatura
cd class-git
code .
Windows:

# Abrir Git Bash como administrador
cd Tecnicatura
cd class-git
code .
📝 Crear y modificar archivo

touch index.html  # Creamos archivo HTML
Agrega un <h1> con tu nombre

Guarda con Ctrl + S

Luego, abre el archivo en el navegador con Live Server (clic derecho → Abrir con Live Server) para ver los cambios. 🌐

💾 Guardar cambios en Git

git status  # Ver estado de archivos

git commit -am "mensaje del commit"  
# Solo funciona con archivos ya creados previamente

git commit -a -m "mensaje del commit"  
# Igual que el anterior

git commit -a  
# Abre VIM para escribir mensaje:  
# esc + i (escribir mensaje)  
# esc  
# :wq! (Windows) o ctrl + x (Linux)  
# s + Enter para confirmar
📜 Ver historial

git log      # Ver historial de commits
q            # Salir

git log --stat  # Ver historial + archivos modificados
q               # Salir
🌿 Trabajar con ramas

git branch        # Ver ramas existentes y en cuál estás
git show          # Muestra el último commit (HEAD apunta aquí)
q                 # Salir

ctrl + l          # Limpiar consola

git branch second  # Crear rama 'second'

git show           # Muestra que HEAD sigue en master, pero el último commit "pega" a dos ramas
q

git status         # Nada para hacer commit

git checkout second  # Cambiar a rama 'second'

git branch           # Ver en qué rama estás

git status           # Ver en qué commit (HEAD) estás apuntando
🖥️ Desde Visual Studio Code (VSC)
Realiza cambios en la rama second para practicar y ver cómo se trabaja con ramas. 💻✨

# 🎓 CLASE 9B - FUSIÓN DE RAMAS

---

## 🔀 ¿Qué es la fusión en Git?

La **fusión** en Git es la forma en que este sistema une un historial bifurcado.  

El comando `git merge` permite integrar líneas de desarrollo independientes, generadas por `git branch`, en una sola rama.

Con este comando podemos crear un nuevo commit que combina dos ramas o *branches*:  
- La rama **actual**  
- La rama que se indica después del comando

---

## ⚠️ Importante

Los comandos de fusión (`merge`) afectan **solo a la rama actual**, no a la rama de destino.  

Por eso, se recomienda:  
- Usar `git checkout` para seleccionar la rama actual  
- Usar `git branch -d` para eliminar ramas de destino que ya no se necesitan

---

## ⚙️ Funcionamiento de `git merge`

- Git merge fusiona secuencias de commits en un solo historial, normalmente para combinar dos ramas.  
- Busca una confirmación base común (commit base) entre ambas ramas.  
- Luego genera una confirmación de fusión que representa la combinación final de ambas ramas.

---

¡Con `git merge` podemos mantener nuestro trabajo organizado y consolidar cambios sin perder el historial! 🚀✨

## 🔀 ¿Cómo unir dos ramas en Git?

Para combinar ramas en tu repositorio local, primero usa `git checkout` para cambiar a la rama donde deseas fusionar los cambios. Por lo general, esta es la rama principal (como `master` o `main`). Luego, emplea `git merge` y especifica el nombre de la otra rama que quieres traer.

### ⚙️ Cómo hacer un merge en Git

Para hacer un merge en Git, primero asegúrate de estar en la rama correcta. Después, usa el comando `git merge` seguido del nombre de la rama que quieres combinar. Por ejemplo, si quieres crear un nuevo commit en la rama `master` con los cambios de la rama `segunda`, usa este comando:

```bash
git checkout master
git merge segunda
⚠️ Nota: En caso de conflictos, guarda tus cambios antes de hacer git checkout para evitar perder tu trabajo. También es recomendable usar comandos básicos de GitHub como git fetch, git push y git pull para mantener actualizado tu repositorio.

🔄 Ejemplo de fusión de ramas
Aquí combinamos los cambios de una rama llamada segunda en master. Otra opción es crear un nuevo commit en la rama segunda combinando los cambios de cualquier otra rama.

Git es asombroso porque sabe qué cambios conservar y cuáles no en una rama. En caso de conflictos, siempre guarda tus cambios antes de cambiar de rama.

🛠 Comandos básicos de GitHub

git init                    # Crear un repositorio (si no existe)
git add .                   # Agregar archivos a staging
git commit -m "mensaje"     # Guardar cambios con mensaje
git branch nombre_rama      # Crear una nueva rama
git checkout nombre_rama    # Cambiar entre ramas
git push origin rama        # Subir cambios al servidor remoto
git fetch                   # Traer actualizaciones del remoto
git merge rama              # Fusionar ramas o guardar cambios remotos
git pull origin rama        # Fetch y merge al mismo tiempo
git checkout "código" archivo  # Volver a versión anterior de archivo
git reset                   # Volver atrás sin posibilidad de recuperar
git reset --soft            # Volver y guardar cambios en staging
git reset --hard            # Restablecer todo al último commit
git reset HEAD              # Quitar cambios de staging (opuesto a git add)
git rm                      # Eliminar archivos y su historial
git rm --cached             # Quitar archivo de staging pero no del disco
git rm --force              # Eliminar archivo de Git y del disco
git status                  # Ver estado de archivos
git log                     # Ver historial de commits
git log --stat              # Cambios específicos por archivo
git show                    # Cambios históricos y específicos
git diff código1 código2    # Comparar dos versiones
git diff                    # Comparar directorio con staging

🚨 Caso práctico: Resolver un conflicto

git status                   # En rama segunda, hacemos cambios y guardamos
git commit -am "Finalizado el cambio en rama segunda"
git status
git checkout master          # Cambios nuevos en master, guardamos
git commit -am "Agregado contenido adicional"
git checkout segunda         # Cambios desaparecen
git checkout master          # Aquí hacemos merge
git merge segunda            # Resolvemos conflictos en VSC, no usar "Fusionar los dos cambios"
git commit -am "Arreglando conflicto"
git status                   # Revisar si algo quedó mal
git commit -am "Solucionado el conflicto 2"
git merge segunda            # Ahora todo va bien
git commit -am "Comentarios adicionales"
git log                      # Ver historial
git checkout segunda
git merge master             # Traemos cambios de master
git commit -am "Actualización desde master"
git checkout master
git merge segunda            # Finalizamos


##CLASE 10A - Resolución de conflictos al hacer merge

### 📚 Sección lectura

Git **nunca borra nada**, a menos que se lo indiquemos explícitamente. Cuando usamos comandos como `git merge` o `git checkout` estamos cambiando de rama o creando un nuevo commit, **no borrando** ramas ni commits (recuerda que para borrar commits se usa `git reset` y para borrar ramas `git branch -d`).

Git es muy inteligente y puede resolver algunos conflictos automáticamente, como cambios en líneas diferentes o nuevas líneas. Pero, cuando dos ramas hacen cambios distintos en **la misma línea**, se produce un **conflicto**.

Este conflicto debemos resolverlo manualmente: hacemos el merge, abrimos el archivo en nuestro editor de código y elegimos qué versión queremos conservar o hacemos una combinación. Editores como **Visual Studio Code** facilitan esto con botones para aceptar o rechazar cambios sin escribir manualmente.

> Siempre debemos crear un nuevo commit para aplicar los cambios del merge.  
> Si Git resuelve el conflicto automáticamente, hará el commit solo.  
> Si no, debemos resolverlo y luego hacer el commit.

Los archivos con conflictos entran en un estado llamado **Unmerged**, parecido al estado Unstaged, es decir, un estado intermedio. Para continuar:

```bash
git add <archivo>   # Para moverlo a staging
git commit          # Para aplicar los cambios en el repositorio
⚠️ Cómo revertir un merge
Si te equivocaste y quieres cancelar el merge antes de hacer commit, usa:


git merge --abort
🌐 Conflictos en repositorios remotos
Al trabajar en equipo, usamos repositorios remotos:

🌻 Para copiar el repositorio remoto al local:


git clone enlace-ssh
Para enviar cambios al remoto:


git push origin master
Para traer actualizaciones del remoto:


git fetch
git merge
Para traer y fusionar en un solo paso:


git pull origin master
🛠 Flujo básico con ramas y conflictos

git branch           # Ver ramas creadas y en cuál estás
git branch second    # Crear nueva rama "second"
git checkout second  # Cambiar a la rama second
# Hacer cambios en el código
ctrl + s             # Guardar cambios
git add .
git commit -m "Cambios en el archivo de trabajo"
git push origin second

git checkout master
git merge second     # Fusionar cambios a master
git push origin master
Para actualizar el repositorio local con cambios remotos:


git fetch
git merge
O con un solo comando:


git pull
⚙️ Comandos útiles
Crear commits rápido (add + commit):


git commit -am "mensaje"
Crear ramas (posicionarse en rama base primero):


git branch nombre_rama
Cambiar de rama:


git checkout nombre_rama
Cambiar nombre por default a la rama principal (a partir de ahora se llamará main):


git config --global init.defaultBranch main
🔄 Práctica: Crear y resolver un conflicto
Hacer cambios en master y guardar:


ctrl + s
git status
git add .
git commit -m "Agregando cambios nuevos al archivo de trabajo"
git push origin master
git log
q  # Salir del log

💻 Cambiar a la rama second y fusionar cambios de master:


git checkout second
git merge master
git push origin second
Crear un conflicto:

Crear o modificar un archivo HTML en second, guardar y commitear:


ctrl + s
git commit -am "Modifiqué el html y el color del texto"
Cambiar a master, modificar el mismo archivo HTML, guardar y commitear:


git checkout master
ctrl + s
git commit -am "Agregué información, cambié el código y puse texto azul"
Intentar hacer merge en master:


git merge second
Se generará un conflicto.

Resolver el conflicto:

Abrir el archivo con conflicto en Visual Studio Code u otro editor.

Seleccionar el cambio que deseas mantener (por ejemplo, "cambio entrante").

Guardar el archivo.

💥Finalizar el proceso:


git status
git commit -am "Solución de conflictos al mergear las ramas"
git checkout second
git merge master          # Pasar cambios de master a second

## 🔐 CLASE 10B - Cómo funcionan las llaves públicas y privadas

### 📚 Sección lectura

Las **llaves públicas y privadas**, también conocidas como **cifrado asimétrico de un solo camino**, se usan para enviar mensajes privados entre varios nodos.  
La lógica es: firmas tu mensaje con una **llave pública** vinculada a una **llave privada** que solo puede leer el mensaje.

🔑 Estas llaves nos ayudan a **cifrar y descifrar archivos** para compartirlos sin riesgo de que sean interceptados por personas malintencionadas.

---

### 🔄 ¿Cómo funciona un mensaje cifrado con llaves públicas y privadas?

1. Ambas personas deben crear su **llave pública** y **llave privada**.

2. Ambas pueden **compartir su llave pública** con las otras partes (🔓 la llave pública es segura para compartir, no importa si la interceptan).

3. La persona que quiere enviar un mensaje **usa la llave pública** del destinatario para **cifrar** el mensaje o archivo.  
   Así, se asegura que solo el destinatario pueda descifrarlo con su llave privada.

4. El mensaje cifrado puede enviarse sin problemas, incluso si alguien lo intercepta.

5. El destinatario utiliza su **llave privada** para **descifrar** el mensaje y acceder al contenido.

---

⚠️ **Importante:**  
🔑 Puedes compartir tu **llave pública** libremente, pero **nunca compartas tu llave privada**.  
La llave privada debe mantenerse siempre segura y confidencial.


CLASE 11 - CONFIGURACIÓN DE LLAVES SSH 🔑

---

### ⚠️ ¿Por qué usar llaves SSH en GitHub?

Si usas solo usuario y contraseña, si pierdes tu PC, todo tu acceso y proyectos están en riesgo.  
Las llaves públicas y privadas agregan una **capa de seguridad más fuerte** y además, ¡ya no tendrás que ingresar usuario y contraseña nunca más! 🚀

---

### 🛠️ ¿Cómo funciona?

- En tu máquina creas una **llave privada** y una **llave pública**.  
- La llave pública la envías a GitHub y le dices: "Para este repositorio, usa esta llave pública".  
- En vez de conectarte por HTTPS, usas el protocolo **SSH**.  
- En la primera conexión, GitHub verifica que tu llave pública esté relacionada con tu llave privada y todo se conecta cifrado automáticamente.  
- Puedes proteger tu llave privada con una contraseña para mayor seguridad. 🔒

---

### ⚙️ Llaves SSH son por persona y máquina, no por proyecto.

---

## 📝 Cómo configurar tus llaves SSH en local

---

### 1. Abrir terminal o Git Bash  
- Windows: Abre Git Bash como administrador  
- Ubuntu: Abre terminal sin entrar a ningún proyecto

---

### 2. Verifica tu configuración de Git

```bash
git config -l
git config --global user.email "alumnos@mail.com"  # Actualiza tu correo
3. Generar tus llaves SSH

ssh-keygen -t rsa -b 4096 -C "alumnos@mail.com"
Te preguntará dónde guardar la llave, presiona Enter para ruta por defecto.

Luego te pedirá una contraseña para proteger la llave privada (¡IMPORTANTE! Recuerda esta contraseña).

4. Iniciar el agente SSH

eval $(ssh-agent -s)
5. Añadir tu llave privada al agente SSH

ssh-add ~/.ssh/id_rsa
Nota:

~ es la carpeta home de tu usuario.

Asegúrate de usar la ruta correcta y el nombre del archivo privado (no el .pub).

6. En MacOS (extra)
Si usas MacOS Sierra (v10.12) o superior, crea o modifica el archivo config en ~/.ssh/ con:

vim

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
Luego añade la llave con:


ssh-add -K ~/.ssh/id_rsa
🔄 Resumen de comandos

git config --global user.email "tu@email.com"
ssh-keygen -t rsa -b 4096 -C "tu@email.com"
eval $(ssh-agent -s)
ssh-add ~/.ssh/id_rsa
🔒 Sobre 2FA (Autenticación de Dos Factores)
Recomendado para mayor seguridad ante robo o pérdida de dispositivos.

Puedes activar 2FA en GitHub desde:

Perfil → Settings

Password and Authentication

Activar GitHub Mobile o Authenticator app (como Twilio Authy) para generar códigos temporales.

👍 Recomendación final
Regístrate y guarda tus datos de 2FA para poder recuperar acceso si cambias de dispositivo.
Esto refuerza muchísimo la seguridad de tus repositorios y cuenta. 🚀🔐


