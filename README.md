# Examen: Héroes, Villanos y Plantillas de Fútbol

## ACLARACIÓN. 

- No esta permitido el uso de IA
- Grabar pantalla y no borrar el video en 7 días
- Permitido el uso de internet para consultar apuntes, código etc.

## 1. Instrucciones de entrega

Partiremos del repositorio inicial facilitado por el profesor.

Cada alumno deberá realizar un **fork** del repositorio original y trabajar sobre su propia copia.

### Pasos iniciales

1. Accede al repositorio original facilitado por el profesor.
2. Pulsa el botón **Fork** para crear una copia en tu cuenta de GitHub.
3. En los ajustes de tu fork, cambia su nombre a:

   `examenVillanos`

4. Comprueba que el repositorio sea **público**.
5. Clona tu repositorio en tu ordenador.
6. Abre el proyecto con PyCharm o Visual Studio Code.

Para clonar el repositorio, utiliza la URL de tu propio fork:

```bash
git clone https://github.com/TU_USUARIO/examenVillanos.git
cd examenVillanos
```

Sustituye `TU_USUARIO` por tu nombre de usuario de GitHub.

**Importante:** todo el trabajo deberá realizarse en este nuevo repositorio, no en el repositorio original del profesor.

## 2. Preparación del entorno

El proyecto está desarrollado en Python. Para trabajar correctamente, deberás crear un entorno virtual e instalar las dependencias.

### 2.1. Crear el entorno virtual

Desde la terminal, situada en la carpeta del proyecto, ejecuta:

```bash
python3 -m venv .venv
```

En Windows puedes utilizar:

```bash
python -m venv .venv
```

### 2.2. Activar el entorno virtual

**macOS / Linux**

```bash
source .venv/bin/activate
```

**Windows (PowerShell)**

```powershell
.venv\Scripts\Activate.ps1
```

### 2.3. Instalar las dependencias

Con el entorno virtual activado, ejecuta:

```bash
python -m pip install -r requirements.txt
```

---

## 3. Normas de trabajo con Git

El examen consta de **cuatro tareas**, cada una desarrollada en su propia rama.

No está permitido desarrollar directamente sobre `main`.

Para cada tarea deberás seguir este procedimiento:

1. Situarte en la rama `main`.
2. Actualizar la rama local.
3. Crear una rama nueva con el nombre indicado.
4. Realizar los cambios correspondientes a esa tarea.
5. Guardar los cambios mediante uno o varios commits.
6. Volver a `main`.
7. Integrar la rama de la tarea mediante un merge local.
8. Subir los cambios a GitHub.


**Normas importantes:**

- Cada tarea debe tener su propia rama.
- Todas las ramas deben crearse a partir de `main` actualizado.
- No se permite trabajar directamente sobre `main`.
- Los merges se realizarán localmente mediante Git.
- No se permite integrar varias tareas en una única rama.
- Los commits deben tener mensajes descriptivos.
- El historial de Git debe permitir comprobar el trabajo realizado en cada tarea.

---

# 4. Tareas del examen

## Rama 1: `001MenuPlantilla`

### Objetivo

Modificar la aplicación actual para que permita elegir entre dos aplicaciones:

- Héroes y Villanos.
- Plantillas de Fútbol.

Al iniciar el programa, deberá mostrarse un menú principal que permita seleccionar la aplicación que se desea utilizar.

La opción de Héroes y Villanos deberá mantener el funcionamiento que ya tenía la aplicación.

Si se selecciona Plantillas de Fútbol, deberá aparecer el siguiente menú:

```text
=================================
       PLANTILLAS DE FÚTBOL
=================================
1. Agregar miembro
2. Listar plantilla
3. Crear plantilla
4. Salir
=================================
```

### Requisitos

- Mantener la aplicación de Héroes y Villanos.
- Incorporar la nueva opción Plantillas de Fútbol.
- Mostrar el menú específico de Plantillas de Fútbol.
- Permitir seleccionar las distintas opciones.
- Controlar las opciones incorrectas.
- Permitir volver al menú principal o salir de la aplicación según el diseño elegido.

**Rama que debes crear:** `001MenuPlantilla`

---

## Rama 2: `002AgregarMiembro`

### Objetivo

Implementar la funcionalidad para agregar miembros a una plantilla de fútbol.

Existirán dos tipos de miembros:

- Jugadores.
- Cuerpo técnico.

Todos los miembros tendrán los siguientes atributos:

- Identificador.
- Nombre.
- Apellidos.

Además, cada tipo tendrá un atributo específico.

### Jugadores

Los jugadores tendrán un atributo adicional:

- `posicion`: cadena de texto (`str`).

La posición podrá ser, por ejemplo, portero, defensa, centrocampista o delantero.

### Cuerpo técnico

Los miembros del cuerpo técnico tendrán un atributo adicional:

- `rol`: cadena de texto (`str`).

Por ejemplo, entrenador o utillero.

### Funcionamiento

Cuando el usuario seleccione **Agregar miembro**, el programa deberá preguntar qué tipo de miembro desea crear:

```text
¿Qué tipo de miembro quieres agregar?

1. Jugador
2. Cuerpo técnico
```

A continuación, solicitará los datos correspondientes al tipo seleccionado.

Los miembros creados deberán almacenarse en un diccionario llamado:

```python
plantilla = {}
```

El identificador de cada miembro se utilizará como clave del diccionario.

El diccionario permitirá almacenar tanto jugadores como miembros del cuerpo técnico.

### Registro en un archivo SQL

Cada vez que se agregue un miembro, se deberá guardar una sentencia SQL en un archivo con extensión `.sql`.

Se utilizará el formato:

```sql
INSERT INTO jugador (id, nombre, apellidos, posicion)
VALUES (1, 'Carlos', 'García López', 'Portero');
```

Para un miembro del cuerpo técnico:

```sql
INSERT INTO miembro (id, nombre, apellidos, rol)
VALUES (24, 'Pedro', 'Martínez Sánchez', 'Entrenador');
```

Los ejemplos son orientativos. Deberás generar las sentencias con los datos introducidos por el usuario.

Requisitos del archivo:

- Debe tener extensión `.sql`.
- Se añadirán las nuevas sentencias sin sobrescribir las anteriores.
- Se generará una sentencia por cada miembro creado.
- Se utilizará la tabla `jugador` para los jugadores y la tabla `miembro` para el cuerpo técnico.
- Los datos de texto deberán tratarse correctamente para no generar sentencias SQL mal formadas.

No es necesario conectarse a una base de datos: el objetivo es generar el archivo de sentencias SQL.

**Rama que debes crear:** `002AgregarMiembro`

---

## Rama 3: `003ListarPlantilla`

### Objetivo

Implementar la opción **Listar plantilla**.

El programa deberá mostrar todos los miembros almacenados en el diccionario `plantilla`.

Se mostrarán los datos comunes y los específicos de cada tipo de miembro.

Por ejemplo:

```text
========== PLANTILLA DE FÚTBOL ==========

ID: 1
Tipo: Jugador
Nombre: Carlos
Apellidos: García López
Posición: Portero
-----------------------------------------

ID: 24
Tipo: Cuerpo técnico
Nombre: Pedro
Apellidos: Martínez Sánchez
Rol: Entrenador
-----------------------------------------
```

### Requisitos

- Recorrer el diccionario `plantilla`.
- Mostrar todos los miembros registrados.
- Mostrar los atributos correspondientes a cada tipo.
- Informar al usuario si la plantilla está vacía.
- Mantener un formato legible y ordenado.

**Rama que debes crear:** `003ListarPlantilla`

---

## Rama 4: `004GenerarPlantilla`

### Objetivo

Implementar la opción **Crear plantilla** para generar automáticamente una plantilla de fútbol mediante la librería Faker.

La plantilla estará formada por 28 miembros: 23 jugadores y 5 miembros del cuerpo técnico.

### Jugadores

Se deberán generar exactamente:

| Posición | Cantidad |
|---|---:|
| Porteros | 2 |
| Defensas | 8 |
| Centrocampistas | 8 |
| Delanteros | 5 |
| **Total** | **23** |

Cada jugador deberá tener:

- Identificador único.
- Nombre.
- Apellidos.
- Posición.

Los nombres y apellidos deberán generarse utilizando Faker.

### Cuerpo técnico

Se deberán generar exactamente:

| Rol | Cantidad |
|---|---:|
| Entrenadores | 1 |
| Utilleros | 4 |
| **Total** | **5** |

Cada miembro del cuerpo técnico deberá tener:

- Identificador único.
- Nombre.
- Apellidos.
- Rol.

También se utilizará Faker para generar sus nombres y apellidos.

### Requisitos

- Generar automáticamente los 28 miembros.
- Si el diccionario tiene datos no se tiene que generar la plantilla
- Respetar las cantidades indicadas para cada posición y rol.
- Guardar todos los miembros en el diccionario `plantilla`.
- Evitar identificadores duplicados.
- No introducir manualmente los nombres de los miembros.
- Utilizar Faker para generar los datos personales.
- Controlar qué ocurre si se selecciona la opción cuando ya existen miembros en la plantilla.

La solución deberá garantizar que se generan las cantidades exactas indicadas.

**Rama que debes crear:** `004GenerarPlantilla`

---

# 5. Entrega del examen

La entrega se realizará mediante un comentario en el lugar indicado por el profesor.

En el comentario deberás incluir la URL de tu repositorio de GitHub.

Ejemplo:

```text
https://github.com/TU_USUARIO/examenVillanos
```

### Condiciones de entrega

- El repositorio deberá ser público.
- El repositorio deberá llamarse `examenVillanos`.
- Deberán estar subidos todos los archivos necesarios para ejecutar la aplicación.
- El historial de Git deberá reflejar el trabajo realizado en las cuatro ramas.
- Las cuatro tareas deberán estar integradas en `main`.
- El proyecto deberá poder ejecutarse siguiendo las instrucciones de este README.
- El código deberá poder ser explicado y defendido por el alumno.

**La entrega no se considerará completa si únicamente se proporciona el código sin el repositorio público y su historial de Git.**

---

# 6. Criterios generales

Se valorará:

- El uso correcto de la programación orientada a objetos.
- La organización del código en clases y módulos.
- El uso de diccionarios para almacenar y consultar los miembros.
- La reutilización del código existente.
- La generación correcta de sentencias SQL.
- El uso de Faker para generar la plantilla.
- El control de errores y de entradas incorrectas.
- La claridad de los mensajes y menús.
- El uso correcto de Git, las ramas, los commits y los merges.
- La capacidad del alumno para explicar el funcionamiento de su solución.

# 7. Rúbrica de evaluación

La calificación máxima del examen será de **10 puntos**. Se evaluará tanto el funcionamiento de la aplicación como la organización del código y el uso correcto de Git.

| Criterio | Descripción | Puntuación |
|---|---|---:|
| **Tarea 1. Menú principal** | Integra las aplicaciones Héroes y Villanos y Plantillas de Fútbol. El menú permite acceder a las opciones solicitadas y controla las entradas incorrectas. | **1,5 puntos** |
| **Tarea 2. Agregar miembro** | Permite crear jugadores y miembros del cuerpo técnico, recoge sus atributos, los almacena correctamente en el diccionario `plantilla` y genera las sentencias SQL en un archivo `.sql`. | **2,5 puntos** |
| **Tarea 3. Listar plantilla** | Recorre el diccionario y muestra correctamente los datos comunes y específicos de cada tipo de miembro. Controla el caso de plantilla vacía. | **1 punto** |
| **Tarea 4. Generar plantilla** | Genera mediante Faker los 23 jugadores y los 5 miembros del cuerpo técnico, respetando las cantidades por posición y rol, con identificadores únicos. | **2 puntos** |
| **Programación orientada a objetos y calidad del código** | Organiza el código en clases y módulos, aplica correctamente la herencia cuando corresponda, reutiliza código y utiliza nombres descriptivos. | **1 punto** |
| **Git y control de versiones** | Crea las cuatro ramas solicitadas, trabaja mediante commits descriptivos e integra cada tarea en `main` mediante merges locales. | **1 punto** |
| **Control de errores y ejecución** | Controla las entradas incorrectas y las excepciones relevantes. La aplicación puede ejecutarse siguiendo las instrucciones del README. | **0,5 puntos** |
| **Documentación y entrega** | El repositorio es público, se llama `examenVillanos`, contiene los archivos necesarios y se entrega la URL mediante un comentario. | **0,5 puntos** |
| | **TOTAL** | **10 puntos** |

## 7.1. Condiciones de evaluación

- Cada criterio se calificará de forma proporcional al grado de cumplimiento de los requisitos.
- Una funcionalidad que no esté implementada no obtendrá puntuación en el apartado correspondiente.
- Si una funcionalidad está implementada parcialmente, se valorará únicamente la parte que funcione correctamente.
- No se valorará únicamente que el programa muestre resultados: se tendrá en cuenta que los datos se almacenen y procesen correctamente.
- Se comprobará que la generación automática de plantillas respeta exactamente las cantidades solicitadas.
- El historial de Git deberá permitir identificar el desarrollo de cada tarea en su rama correspondiente.
- El alumno deberá ser capaz de explicar y defender el código entregado. Si no puede justificar su funcionamiento, la autoría o las decisiones de implementación, la calificación podrá verse afectada conforme a las normas de evaluación del módulo.

## 7.2. Distribución por tareas

| Tarea | Puntuación máxima |
|---|---:|
| `001MenuPlantilla` | 1,5 puntos |
| `002AgregarMiembro` | 2,5 puntos |
| `003ListarPlantilla` | 1 punto |
| `004GenerarPlantilla` | 2 puntos |
| Calidad del código y POO | 1 punto |
| Git y control de versiones | 1 punto |
| Control de errores y ejecución | 0,5 puntos |
| Documentación y entrega | 0,5 puntos |
| **Total** | **10 puntos** |


**Recuerda:** el objetivo no es únicamente que el programa funcione, sino demostrar que sabes desarrollar, organizar y versionar una aplicación Python.
