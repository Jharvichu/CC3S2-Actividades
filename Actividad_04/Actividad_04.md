#### Ejercicios

##### Ejercicio 1: Manejo avanzado de ramas y resolución de conflictos

**Objetivo:** Practicar la creación, fusión y eliminación de ramas, así como la resolución de conflictos que puedan surgir durante la fusión.

1. **Crear una nueva rama para una característica:**
   - Creamos una nueva rama llamada `feature/advanced-feature` desde la rama `main`:

    <img src="Imagenes/Ejercicio1_01.png" width="600">

2. **Modificar archivos en la nueva rama:**
   - Editamos el archivo `main.py` para incluir una función adicional:
     ```python
     def greet():
         print('Hello from advanced feature')

     greet()
     ```
   - Añadimos y confirmamos estos cambios en la rama `feature/advanced-feature`:

    <img src="Imagenes/Ejercicio1_02.png" width="600">

3. **Simular un desarrollo paralelo en la rama main:**
   - Cambiamos de nuevo a la rama `main` con el siguiente comando:

     ```bash
     $ git checkout main
     ```
   - Editamos el archivo `main.py` de forma diferente (por ejemplo, cambia el mensaje del print original):
     ```python
     print('Hello World - updated in main')
     ```
   - Añadimos y confirmamos estos cambios en la rama `main`:

     ```bash
     $ git add main.py
     $ git commit -m "Actualizacion del mensaje de main.py en la rama main"
     ```

4. **Intentar fusionar la rama feature/advanced-feature en main:**
   - Fusionamos la rama `feature/advanced-feature` en `main`:

    <img src="Imagenes/Ejercicio1_03.png" width="600">

5. **Resolver el conflicto de fusión y eliminar rama fusionada:**
   - Git generará un conflicto en `main.py`. Abre el archivo y resuelve el conflicto manualmente, elegimo combinar las dos versiones.

    <img src="Imagenes/Ejercicio1_04.png" width="600">

   - Después de resolver el conflicto, añade el archivo resuelto y completa la fusión, ademas eliminamos la rama:

     <img src="Imagenes/Ejercicio1_05.png" width="600">


#### Ejercicio 2: Exploración y manipulación del historial de commits

**Objetivo:** Aprender a navegar y manipular el historial de commits usando comandos avanzados de Git.

1. **Ver el historial detallado de commits:**
   - Usa el comando `git log` para explorar el historial de commits, pero esta vez con más detalle:

     ```bash
     $ git log -p
     ```
    <img src="Imagenes/Ejercicio2_01.png" width="600">

   - Examina las diferencias introducidas en cada commit. ¿Qué cambios fueron realizados en cada uno?

    Una diferencia notoria es en los hash'es de cada commit, difieren en todos sus caracteres. Ademas los cambios realizados fueron lo que hicimos al main.py para el ejercicio anterior. Otra diferencia, no tan importante es en la fecha que se hizo el commit.

2. **Filtrar commits por autor:**
   - Usamos el siguiente comando para mostrar solo los commits realizados por un autor, en este caso Jharvy:

     ```bash
     $ git log --author="Jharvy"
     ```
    <img src="Imagenes/Ejercicio2_02.png" width="600">

3. **Revertir un commit:**
   - Imagina que el commit más reciente en `main.py` no debería haberse hecho. Usa `git revert` para revertir ese commit:

     ```bash
     $ git revert HEAD
     ```
   - Verifica que el commit de reversión ha sido añadido correctamente al historial.

    Agregue algunos comentarios en `main.py` para ejecutar el comando y se pueda visualizar mejor.

    <img src="Imagenes/Ejercicio2_03.png" width="600">

4. **Rebase interactivo:**
   - Usa el siguiente comando para empezar el rebase interactivo:

     ```bash
     $ git rebase -i HEAD~3
     ```
   - En el editor que se abre, combina los últimos tres commits en uno solo utilizando la opción `squash`.

    <img src="Imagenes/Ejercicio2_04.png" width="600">

    Despues de hacer el rebase, tenemos:

    <img src="Imagenes/Ejercicio2_05.png" width="600">

5. **Visualización gráfica del historial:**
   - Usamos el siguiente comando para ver una representación gráfica del historial de commits:

    <img src="Imagenes/Ejercicio2_06.png" width="600">

   - Reflexiona sobre cómo el historial de tu proyecto se visualiza en este formato. ¿Qué información adicional puedes inferir?

   Se visualiza de forma cronologica y de forma estructurada, util para tener conocimiento del trabajo paralelo o de como ha evolucionado el proyecto. Una informacion que se puede inferir es que rama se a trabajado más. Posibles ramas con errores potenciales.


#### Ejercicio 3: Creación y gestión de ramas desde commits específicos

**Objetivo:** Practicar la creación de ramas desde commits específicos y comprender cómo Git maneja las referencias históricas.

1. **Crear una nueva rama desde un commit específico:**
   - Usamos el historial de commits (`git log --oneline`) para identificar un commit antiguo desde el cual crear una nueva rama:

     ```bash
     $ git log --oneline
     ```
   - Creamos una nueva rama `bugfix/rollback-feature` desde ese commit:

    <img src="Imagenes/Ejercicio3_01.png" width="600">
    
2. **Modificar y confirmar cambios en la nueva rama:**
   - Realizamos algunas modificaciones en `main.py` que simulen una corrección de errores:
     ```python
     def greet():
         print('Fixed bug in feature')
     ```
   - Añadimos y confirma los cambios en la nueva rama:

    <img src="Imagenes/Ejercicio3_02.png" width="600">

3. **Fusionar los cambios en la rama principal:**
   - Cambia de nuevo a la rama `main` y fusiona la rama `bugfix/rollback-feature`:

    <img src="Imagenes/Ejercicio3_03.png" width="600">

4. **Explorar el historial después de la fusión:**
   - Usa `git log` y `git log --graph` para ver cómo se ha integrado el commit en el historial:

    <img src="Imagenes/Ejercicio3_04.png" width="600">

5. **Eliminar la rama bugfix/rollback-feature:**
   - Una vez fusionados los cambios, eliminamos la rama `bugfix/rollback-feature`:

    <img src="Imagenes/Ejercicio3_05.png" width="600">


#### Ejercicio 4: Manipulación y restauración de commits con git reset y git restore

**Objetivo:** Comprender cómo usar `git reset` y `git restore` para deshacer cambios en el historial y en el área de trabajo.

1. **Hacer cambios en el archivo main.py:**
   - Editamos el archivo `main.py` para introducir un nuevo cambio:
     ```python
     print('This change will be reset')
     ```
   - Añade y confirma los cambios:

    <img src="Imagenes/Ejercicio4_01.png" width="600">

2. **Usar git reset para deshacer el commit:**
   - Deshaz el commit utilizando `git reset` para volver al estado anterior:

     ```bash
     $ git reset --hard HEAD~1
     ```
   - Verifica que el commit ha sido eliminado del historial y que el archivo ha vuelto a su estado anterior.

    <img src="Imagenes/Ejercicio4_02.png" width="600">

3. **Usar git restore para deshacer cambios no confirmados:**
   - Realiza un cambio en `README.md` y no lo confirmes:

     ```bash
     $ echo "Another line in README" >> README.md
     $ git status
     ```

    <img src="Imagenes/Ejercicio4_03.png" width="600">

   - Usa `git restore` para deshacer este cambio no confirmado:

     ```bash
     $ git restore README.md
     ```
   - Verifica que el cambio no confirmado ha sido revertido.

    <img src="Imagenes/Ejercicio4_04.png" width="600">


#### Ejercicio 5: Trabajo colaborativo y manejo de Pull Requests

**Objetivo:** Simular un flujo de trabajo colaborativo utilizando ramas y pull requests.

1. **Crear un nuevo repositorio remoto:**
   - Usa GitHub o GitLab para crear un nuevo repositorio remoto y clónalo localmente con:

     ```bash
     $ git clone <URL-del-repositorio>
     ```

    En este caso ya lo tenia clonado, asi que omitimos esta parte.

2. **Crear una nueva rama para desarrollo de una característica:**
   - En tu repositorio local, crea una nueva rama `feature/team-feature`:

    <img src="Imagenes/Ejercicio5_01.png" width="600">

3. **Realizar cambios y enviar la rama al repositorio remoto:**
   - Realizamos cambios en los archivos del proyecto y confírmalos:

     ```bash
     $ echo "print('Collaboration is key!')" > collaboration.py
     $ git add .
     $ git commit -m "Add collaboration script"
     ```
   - Envíamos la rama al repositorio remoto:

     ```bash
     $ git push origin feature/team-feature
     ```

    <img src="Imagenes/Ejercicio5_02.png" width="600">


4. **Abrir un Pull Request:**
   - Abre un Pull Request (PR) en la plataforma remota (GitHub/GitLab) para fusionar `feature/team-feature` con la rama `main`.
   - Añade una descripción detallada del PR, explicando los cambios realizados y su propósito.
    <img src="Imagenes/Ejercicio5_03.png" width="600">


5. **Revisar y fusionar el Pull Request:**
   - Simula la revisión de código, comenta en el PR y realiza cualquier cambio necesario basado en la retroalimentación.
   - Una vez aprobado, fusiona el PR en la rama `main`.
    <img src="Imagenes/Ejercicio5_04.png" width="600">

6. **Eliminar la rama remota y local:**
   - Después de la fusión, eliminaMOS la rama tanto local como remotamente:
    <img src="Imagenes/Ejercicio5_05.png" width="600">
    

#### Ejercicio 6: Cherry-Picking y Git Stash

**Objetivo:** Aprender a aplicar commits específicos a otra rama utilizando `git cherry-pick` y a guardar temporalmente cambios no confirmados utilizando `git stash`.

**Instrucciones:**

1. **Hacer cambios en main.py y confirmarlos:**
   - Realizamos y confirmamos varios cambios en `main.py` en la rama `main`:
    <img src="Imagenes/Ejercicio6_01.png" width="600">
    

2. **Crear una nueva rama y aplicar el commit específico:**
   - Crea una nueva rama `feature/cherry-pick` y aplícale el commit específico:

     ```bash
     $ git branch feature/cherry-pick
     $ git checkout feature/cherry-pick
     $ git cherry-pick <commit-hash>
    ```
  <img src="Imagenes/Ejercicio6_02.png" width="600">


3. **Guardar temporalmente cambios no confirmados:**
   - Realiza algunos cambios en `main.py` pero no los confirmamos, y ademas guardamos temporalmente con el comando `git stash`:

   <img src="Imagenes/Ejercicio6_03.png" width="600"> 

4. **Aplicar los cambios guardados:**
   - Realiza otros cambios y confírmalos si es necesario.

   <img src="Imagenes/Ejercicio6_04.png" width="600"> 

   - Luego, recuperaMOS los cambios guardados anteriormente:

    <img src="Imagenes/Ejercicio6_05.png" width="600"> 

5. **Revisar el historial y confirmar la correcta aplicación de los cambios:**

   - UsaMOS `git log` para revisar el historial de commits y verificar que todos los cambios se han aplicado correctamente.

   <img src="Imagenes/Ejercicio6_06.png" width="600"> 