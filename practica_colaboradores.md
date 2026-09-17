# Guía de Práctica: Trabajo Colaborativo con Git y GitHub

## Introducción

Esta práctica tiene como objetivo simular un flujo de trabajo colaborativo real utilizando **Git** y **GitHub**. Participarán dos usuarios con roles diferenciados:

- **usuario-uniajc-prof**: Administrador del proyecto (crea el repositorio, invita colaboradores, revisa y fusiona cambios).
- **usuario-uniajc-admon**: Colaborador (clona el repositorio y realiza aportes).

Al finalizar, los estudiantes comprenderán cómo múltiples desarrolladores pueden trabajar simultáneamente en un proyecto, utilizando ramas, Pull Requests y resolviendo conflictos.


## Objetivos de aprendizaje

1. Crear y configurar un repositorio remoto en GitHub.
2. Invitar colaboradores y gestionar permisos.
3. Clonar un repositorio y trabajar con ramas.
4. Realizar commits y push a ramas remotas.
5. Crear, revisar y fusionar Pull Requests.
6. Resolver conflictos de merge.


## Fase 1: Configuración inicial (usuario-uniajc-prof)

### Paso 1: Crear el proyecto local

Crea una carpeta para el proyecto y dentro de ella los archivos `index.html` y `style.css`.

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <nav>
            <ul>
                <li><a href="index.html" class="active">Inicio</a></li>
                <li><a href="profesores.html">Profesores</a></li>
                <li><a href="estudiantes.html">Estudiantes</a></li>
                <li><a href="contacto.html">Contáctenos</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <h2>Bienvenidos</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Aperiam beatae voluptatibus molestias incidunt ipsa doloribus eius eaque, rem aliquam, tempore repudiandae numquam voluptate hic maxime necessitatibus. Velit alias et tempora aut quod facilis unde, ducimus asperiores ullam quia eligendi labore recusandae dolor, explicabo dolorem fuga magnam quos fugit dignissimos? Illum?</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae amet dignissimos deserunt possimus quam natus doloribus et rerum, laudantium veritatis mollitia voluptates impedit soluta eveniet quas at eius eligendi, sapiente repellendus! Iste quia dolor maxime. Odio qui quidem, velit nam nisi cupiditate perspiciatis voluptatum non expedita, aliquam exercitationem eum fugit facere suscipit ratione possimus? Eum expedita, mollitia sint, in sapiente dolorem modi itaque sunt nemo quas cupiditate corrupti maiores voluptate.</p>
    </main>
</body>
</html>
```

**style.css**

```css
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f9f9f9;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

header {
    background-color: #ffffff;
    border-bottom: 2px solid #2c6e49;
    padding: 1rem 2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

/* ===== Menú de navegación ===== */
nav ul {
    list-style: none;
    display: flex;
    gap: 1.5rem;
    flex-wrap: wrap;
}

nav a {
    text-decoration: none;
    color: #333;
    font-weight: 500;
    padding: 0.4rem 0.8rem;
    border-radius: 4px;
    transition: background-color 0.2s, color 0.2s;
}

nav a:hover {
    background-color: #e8f5ef;
    color: #2c6e49;
}

nav a.active {
    background-color: #2c6e49;
    color: #ffffff;
}

/* ===== Contenido principal ===== */
main {
    flex: 1;
    max-width: 1100px;
    margin: 2rem auto;
    padding: 2rem;
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
    width: calc(100% - 2rem);
}

main h2 {
    color: #2c6e49;
    margin-bottom: 1rem;
    border-bottom: 2px solid #e8f5ef;
    padding-bottom: 0.5rem;
}
```

### Paso 2: Inicializar el repositorio Git local

Abre una terminal en la carpeta del proyecto y ejecuta:

```bash
git init
git add .
git commit -m "Pagina inicial"
```

**Explicación:**
- `git init`: Crea un repositorio Git local en la carpeta actual.
- `git add .`: Agrega todos los archivos al área de preparación (staging).
- `git commit -m "..."`: Guarda los cambios en el historial local con un mensaje descriptivo.

### Paso 3: Crear el repositorio remoto en GitHub

1. Inicia sesión en GitHub con la cuenta **usuario-uniajc-prof**.
2. Haz clic en **New repository**.
3. Asigna el nombre **prueba-general**.
4. Deja el repositorio como público o privado según prefieras.
5. **No** inicialices con README, .gitignore ni licencia (ya tienes archivos locales).
6. Haz clic en **Create repository**.

### Paso 4: Conectar el repositorio local con el remoto

```bash
git remote add origin https://github.com/usuario-uniajc-prof/prueba-general.git
git push -u origin main
```

**Explicación:**
- `git remote add origin <url>`: Vincula el repositorio local con el remoto.
- `git push -u origin main`: Sube la rama `main` al remoto y establece el seguimiento (`-u`).

> **Nota:** Si tu rama principal se llama `master`, reemplaza `main` por `master`. Puedes renombrarla con `git branch -M main`.

### Paso 5: Invitar al colaborador

1. En GitHub, ve a **Settings** → **Collaborators**.
2. Haz clic en **Add people**.
3. Busca y agrega a **usuario-uniajc-admon**.
4. Envía la invitación.


## Fase 2: El colaborador acepta y clona (usuario-uniajc-admon)

### Paso 1: Aceptar la invitación

Revisa tu correo o notificaciones en GitHub y acepta la invitación para colaborar en el repositorio.

### Paso 2: Clonar el repositorio

```bash
git clone https://github.com/usuario-uniajc-prof/prueba-general.git
cd prueba-general
```

**Explicación:**
- `git clone <url>`: Descarga una copia completa del repositorio remoto.
- `cd prueba-general`: Ingresa a la carpeta del proyecto.


## Fase 3: Trabajo en ramas (usuario-uniajc-prof)

### Paso 1: Crear una rama para la nueva funcionalidad

```bash
git checkout -b dev-profesores
```

**Explicación:**
- `git checkout -b <rama>`: Crea y cambia a una nueva rama llamada `dev-profesores`.

### Paso 2: Crear el archivo `profesores.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profesores - Instituto Académico del Valle</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">
                <h1>Instituto Académico del Valle</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="index.html">Inicio</a></li>
                    <li><a href="profesores.html" class="active">Profesores</a></li>
                    <li><a href="estudiantes.html">Estudiantes</a></li>
                    <li><a href="contacto.html">Contáctenos</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main>
        <h2>Nuestros Profesores</h2>
        <p>
            Contamos con un equipo docente altamente calificado, comprometido con la
            formación de los estudiantes y la excelencia académica.
        </p>
    </main>
</body>
</html>
```

### Paso 3: Confirmar y subir los cambios

```bash
git add .
git commit -m "agregue pagina profesores.html"
git push -u origin dev-profesores
```

**Explicación:**
- Se agrega el nuevo archivo, se confirma y se sube la rama `dev-profesores` al repositorio remoto.


## Fase 4: Trabajo en ramas (usuario-uniajc-admon)

### Paso 1: Actualizar el repositorio local

```bash
git pull
```

**Explicación:** Descarga los últimos cambios del remoto (aunque aún no ve la rama `dev-profesores` porque está en otra rama).

### Paso 2: Crear una rama para su funcionalidad

```bash
git checkout -b dev-estudiantes
```

### Paso 3: Crear el archivo `estudiantes.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estudiantes - Instituto Académico del Valle</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">
                <h1>Instituto Académico del Valle</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="index.html">Inicio</a></li>
                    <li><a href="profesores.html">Profesores</a></li>
                    <li><a href="estudiantes.html" class="active">Estudiantes</a></li>
                    <li><a href="contacto.html">Contáctenos</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main>
        <h2>Información para Estudiantes</h2>
        <p>
            En el Instituto Académico del Valle ofrecemos diferentes programas académicos
            diseñados para acompañar el desarrollo integral de nuestros estudiantes.
        </p>
    </main>
</body>
</html>
```

### Paso 4: Confirmar y subir los cambios

```bash
git add .
git commit -m "agregue estudiantes.html"
git push -u origin dev-estudiantes
```


## Fase 5: Pull Requests y fusión

### Pull Request de `dev-profesores`

Con el usuario **usuario-uniajc-prof**, en GitHub:

1. Ve a la pestaña **Pull requests**.
2. Haz clic en **New pull request**.
3. Selecciona como base `main` y como compare `dev-profesores`.
4. Verifica que no haya conflictos. GitHub mostrará los cambios.
5. Haz clic en **Create pull request**.
6. Agrega un título y descripción.
7. Haz clic en **Create pull request**.
8. Agrega un comentario si lo deseas y haz clic en **Comment**.
9. Haz clic en **Merge pull request**.
10. Escribe un mensaje de commit y confirma con **Confirm merge**.

### Pull Request de `dev-estudiantes`

Repite el mismo proceso con la rama `dev-estudiantes`. Como no hay conflictos (cada uno creó archivos distintos), la fusión será directa.


## Fase 6: Caso de colisión (conflicto)

Para simular un conflicto, ambos usuarios modificarán el mismo archivo `index.html` en sus respectivas ramas.

### Usuario-uniajc-prof

1. Crea una nueva rama:
   ```bash
   git checkout -b feature-footer
   ```
2. Modifica `index.html` agregando un **footer** antes del cierre de `</body>`:

   ```html
   <footer>
       <p><strong>Instituto Académico del Valle</strong></p>
       <p>Calle 15 #25-30, San Fernando · Cali, Valle del Cauca, Colombia</p>
       <p>© <span id="anio"></span> Todos los derechos reservados.</p>
   </footer>

   <script src="script.js"></script>
   ```

3. Crea el archivo `script.js`:

   ```js
   // Actualiza dinámicamente el año en el footer
   document.addEventListener("DOMContentLoaded", function () {
       const anioActual = new Date().getFullYear();
       const elementoAnio = document.getElementById("anio");
       if (elementoAnio) {
           elementoAnio.textContent = anioActual;
       }

       // Mensaje de bienvenida en la consola (solo como ejemplo de JS)
       console.log("Bienvenido al sitio del Instituto Académico del Valle");
   });
   ```

4. Confirma y sube:
   ```bash
   git add .
   git commit -m "agregue footer y script"
   git push -u origin feature-footer
   ```

### Usuario-uniajc-admon

1. Actualiza su rama principal y crea una nueva rama:
   ```bash
   git checkout main
   git pull
   git checkout -b feature-parrafo
   ```
2. Modifica `index.html` agregando un **párrafo adicional** dentro del `<main>`:

   ```html
   <p>Este es un párrafo adicional agregado por el colaborador para demostrar el trabajo en equipo.</p>
   ```

3. Confirma y sube:
   ```bash
   git add .
   git commit -m "agregue parrafo adicional"
   git push -u origin feature-parrafo
   ```

### Crear Pull Requests y resolver conflicto

1. Ambos usuarios crean Pull Requests hacia `main`.
2. El primero en fusionar (por ejemplo, `feature-footer`) no tendrá problemas.
3. El segundo Pull Request (`feature-parrafo`) mostrará un **conflicto** porque el archivo `index.html` fue modificado en la misma zona (aunque en partes distintas, Git puede detectarlo si están cerca).
4. GitHub indicará que hay conflictos. El usuario debe resolverlos localmente:

   ```bash
   git checkout feature-parrafo
   git pull origin main
   ```

   Git marcará el conflicto en `index.html`. Edita el archivo para combinar ambos cambios (footer y párrafo). Luego:

   ```bash
   git add index.html
   git commit -m "resolvi conflicto en index.html"
   git push origin feature-parrafo
   ```

5. El Pull Request se actualizará y ya no mostrará conflictos. Se procede a fusionar.


## Fase 7: Limpieza de ramas

Una vez fusionadas las ramas, se pueden eliminar local y remotamente:

```bash
git checkout main
git branch -d nombre-de-la-rama
git push origin --delete nombre-de-la-rama
```

**Explicación:**
- `git branch -d <rama>`: Elimina la rama local (solo si ya fue fusionada).
- `git push origin --delete <rama>`: Elimina la rama remota.


## Resumen de comandos utilizados

| Comando | Descripción |
|---------|-------------|
| `git init` | Inicializa un repositorio local |
| `git add .` | Agrega todos los cambios al staging |
| `git commit -m "mensaje"` | Confirma los cambios |
| `git remote add origin <url>` | Vincula el repositorio local con el remoto |
| `git push -u origin <rama>` | Sube una rama al remoto y establece seguimiento |
| `git clone <url>` | Clona un repositorio remoto |
| `git checkout -b <rama>` | Crea y cambia a una nueva rama |
| `git pull` | Descarga y fusiona cambios del remoto |
| `git branch -d <rama>` | Elimina una rama local |
| `git push origin --delete <rama>` | Elimina una rama remota |


## Conclusiones

Esta práctica demuestra el flujo de trabajo colaborativo típico en proyectos de software:

- El administrador configura el repositorio y gestiona los permisos.
- Los colaboradores trabajan en ramas independientes para no interferir entre sí.
- Los Pull Requests permiten revisar y discutir cambios antes de integrarlos.
- Los conflictos son normales y se resuelven manualmente.
- La limpieza de ramas mantiene el repositorio ordenado.

Este conocimiento es fundamental para cualquier desarrollador que trabaje en equipo.
