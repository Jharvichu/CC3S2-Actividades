# Ejercicios
### Ejercicio 1: Manejo avanzado de ramas y resolución de conflictos
**Objetivo**:  Practicar la creación, fusión y eliminación de ramas, así como la resolución de conflictos que puedan surgir durante la fusión.
1. **Crear una nueva rama para una característica:**
   - Crea una nueva rama llamada `feature/rama-avanzada` desde la rama `main`:
     ```bash
	 
     ```

2. **Modificar archivos en la nueva rama:**
   - Editamos el archivo `main.py` para incluir una función adicional:
     ```python
     def greet():
         print('Hello from advanced feature')

     greet()
     ```
   - Añadimos y confirmamos estos cambios en la rama `feature/rama-avanzada`:

     ```bash
     ```

3. **Simular un desarrollo paralelo en la rama main:**
   - Cambiamos de nuevo a la rama `main`:

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
     $ git commit -m "Update main.py message in main branch"
     ```

4. **Intentar fusionar la rama feature/advanced-feature en main:**
   - Fusionamos la rama `feature/advanced-feature` en `main`:

     ```bash
     $ git merge feature/advanced-feature
     ```

5. **Resolver el conflicto de fusión:**
   - Git generará un conflicto en `main.py`. Abrimo el archivo y resolvemos el conflicto manualmente, eligiendo combinar las dos versiones.
   - Después de resolver el conflicto, añadimos el archivo resuelto y completamos la fusión:

     ```bash
     $ git add main.py
     $ git commit -m "Resolve merge conflict between main and feature/advanced-feature"
     ```

6. **Eliminar la rama fusionada:**
   - Una vez que fusionamos con éxito y resuelto los conflictos, elimina la rama `feature/advanced-feature`:

     ```bash
     $ git branch -d feature/advanced-feature
     ```

#### Ejercicio 2: Exploración y manipulación del historial de commits

**Objetivo:** Aprender a navegar y manipular el historial de commits usando comandos avanzados de Git.

1. **Ver el historial detallado de commits:**
   - Usa el comando `git log` para explorar el historial de commits, pero esta vez con más detalle:

     ```bash
     $ git log -p
     ```
   - Examina las diferencias introducidas en cada commit. ¿Qué cambios fueron realizados en cada uno?

   Algunos cambios en los commits que observo son en los hash, esas linea de caracteres no se repide en ningun commit. Otro cambio no tan resaltante es en la fecha que se dio el commit y el mensaje que describe el commit.

2. **Filtrar commits por autor:**
   - Usa el siguiente comando para mostrar solo los commits realizados por un autor específico:

     ```bash
     $ git log --author="TuNombre"
     ```

3. **Revertir un commit:**
   - Imagina que el commit más reciente en `main.py` no debería haberse hecho. Usa `git revert` para revertir ese commit:

     ```bash
     $ git revert HEAD
     ```
   - Verifica que el commit de reversión ha sido añadido correctamente al historial.

4. **Rebase interactivo:**
   - Realiza un rebase interactivo para combinar varios commits en uno solo. Esto es útil para limpiar el historial de commits antes de una fusión.
   - Usa el siguiente comando para empezar el rebase interactivo:

     ```bash
     $ git rebase -i HEAD~3
     ```
   - En el editor que se abre, combina los últimos tres commits en uno solo utilizando la opción `squash`.

5. **Visualización gráfica del historial:**
   - Usa el siguiente comando para ver una representación gráfica del historial de commits:

     ```bash
     $ git log --graph --oneline --all
     ```
   - Reflexiona sobre cómo el historial de tu proyecto se visualiza en este formato. ¿Qué información adicional puedes inferir?

