# Bitácora de Git y GitHub - Basada en el Curso de platzi.

**Autor:** David Francisco Sanchez

## 1. Configuración del Entorno y Fundamentos

El desarrollo se realizó preparando un entorno Linux nativo dentro de Windows para garantizar la compatibilidad con las herramientas de Git.

### Instalación de WSL y Ubuntu

La preparación del sistema se realizó a través de Windows PowerShell:

1. **Habilitación de WSL:** Uso del comando `wsl --install`.
2. **Cambio de Versión:** Configuración a versión 1 mediante:
   `wsl --set-default-version 1`
3. **Instalación de Ubuntu:** Configuración de **Ubuntu** desde la Microsoft Store.

### Configuración Global de Git

- **Identidad:**  
    - `git config --global user.name "Usuario-GitHub"`
    - `git config --global user.email "tu-correo@ejemplo.com"`
- **Rama por Defecto:** Establecimiento de `main` como rama inicial:
    `git config --global init.defaultBranch main`
- **Comandos de Terminal (Ubuntu):** Gestión con `ls`, `cd`, `mkdir` y `pwd`.
- **Integración con IDE:** Apertura de Visual Studio Code con `code .`.

## 2. El Ciclo de Vida del Archivo y Áreas de Trabajo

Git gestiona los cambios a través de zonas lógicas que permiten un control total antes de la persistencia:

- **Local:**
    - Directorio de Trabajo (Working Directory).
    - Área de Preparación (Staging Area): Uso de `git add`.
    - Repositorio Local (.git): Uso de `git commit`.

- **Remoto:**
    - GitHub: Almacenamiento y colaboración en la nube.

### Gestión de Historial

- `git status`: Diagnóstico del estado de los archivos.
- `git log`: Visualización de la lista de commits.
- `git rm`: Eliminación de archivos del rastreo.

## 3. Control de Versiones y Gestión de Tiempos

- **Ramas (Branching):** Navegación con `git branch`, `git checkout` y `git switch`.
- **Configuración de Pull (Estrategias):**
    - `git config pull.rebase false`: Fusión estándar (Merge commit).
    - `git config pull.rebase true`: Reorganización del historial (Rebase).
    - `git config pull.ff`: Configuración de avance rápido (Fast-forward).
- **Estados de Reset:**
    - `--soft`: Mantiene cambios en Staging.
    - `--mixed`: Mantiene cambios en el directorio de trabajo.
    - `--hard`: Borra todos los cambios para volver a un estado anterior.
- **Recuperación:** Uso de `git revert` para deshacer cambios y `git stash` para guardado temporal.

## 4. Colaboración y Seguridad en GitHub

- **Autenticación:** Configuración de llaves SSH y Personal Access Tokens (PAT) clásicos y detallados.
- **Sincronización:** Flujo mediante `git push` (subir), `git fetch` (inspeccionar) y `git pull` (bajar y unir).
- **Herramientas:** Pull Requests (PR), Issues, GitHub Gist y Forks.

## 5. Flujo de Trabajo y Buenas Prácticas

Se implementó un flujo lineal para asegurar la estabilidad del proyecto:

1. **Nueva Rama:** `git switch -c rama-nueva` (Trabajo aislado).
2. **Cambios:** `git add` y `git commit` (Guardado local).
3. **Publicar:** `git push origin rama-nueva` (Subir a GitHub).
4. **Revisar:** Crear **Pull Request** en GitHub (Validación).
5. **Fusionar:** Merge a la rama `main` y eliminación de la rama temporal.

### Diagrama del Flujo (Mermaid)

[visualizador de diagramas de mermaid](https://mermaid.live/edit#pako:eNpVkc1ugzAQhF_F2lMrkYifgIkPlRrS5pKqPeQUyMEKG4wSbGSM0hR49xqiqu2edjTzzR62g6PKERicLup6FFwbsltnkth5ThOhy8ZUvDmQ2eyp36AhlZJ468nqYaNII1Rdl7J4vOdXY4gk3XaMITGilOfhbiUT_y6xJ-t0y2uj6sNfZ3dVPXlJyw9h6_87QqOlXtMTZyc-O3JNEq4P4EChyxyY0S06UKGu-CihG-EMjMAKM2B2zbk-Z5DJwTI1l3ulqh9Mq7YQYHsvjVVtnXOD65IXmv9GUOaoE9VKA8xbBlMHsA4-rYyX88Dz4iCI6IKGNPIduAHz4_kioIs4DELXX0Z-RAcHvqaz7jymoWvHj1xKXT_0HMC8NEq_3b8wPWP4Bi_ue5I)

```mermaid
graph LR
  A[Nueva Rama] --> B[Add / Commit]
  B --> C[Push GitHub]
  C --> D[Pull Request]
  D --> E[Merge a Main]
