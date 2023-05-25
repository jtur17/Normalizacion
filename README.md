# Normalización

## Ejercicio 1FN

| CodLibro | Titulo              | CodAutor | Autor                    | TelefonoEditorial | Editorial    | CodLector | NombreLector             | CodDevolucion | FechaDev    |
|----------|---------------------|----------|--------------------------|-------------------|--------------|-----------|--------------------------|---------------|-------------|
| 1001     | Variable Compleja   | 1        | Murray Spiegel           | 123456789         | McGraw Hill  | 1         | Pérez Gómez, Juan        | 1             | 15/04/2014  |
| 1004     | Visual Basic        | 2        | E. Petroustsos           | 987654321         | Anaya        | 2         | Ríos Terán, Ana          | 2             | 17/04/2014  |
| 1005     | Estadística         | 1        | Murray Spiegel           | 123456789         | McGraw Hill  | 3         | Roca García René         | 3             | 16/04/2014  |
| 1006     | Oracle University   | 3        | Nancy Greenberg          | 789123456         | Oracle Corp. | 4         | García Roque, Luis       | 4             | 20/04/2014  |
| 1007     | Clipper 5.01        | 5        | Ramalho                  | 123456789         | McGraw Hill  | 5         | Pérez Gómez, Juan        | 5             | 18/04/2014  |



### Solución

Esta tabla no cumple el requisito **1NF** de sólo tener campos atómicos, ya que el nombre del lector es un campo en el que se puede dividir en dos columnas más, en primer apellido y segundo apellido, tal como lo muestra la siguiente tabla.

| CodLibro | Titulo              | CodAutor | Autor                    | TelefonoEditorial | Editorial    | CodLector | Paterno | Materno | Nombres | CodDevolucion | FechaDev    |
|----------|---------------------|----------|--------------------------|-------------------|--------------|-----------|---------|---------|---------|---------------|-------------|
| 1001     | Variable Compleja   | 1        | Murray Spiegel           | 123456789         | McGraw Hill  | 1         | Pérez   | Gómez   | Juan    | 1             | 15/04/2014  |
| 1004     | Visual Basic        | 2        | E. Petroustsos           | 987654321         | Anaya        | 2         | Ríos    | Terán   | Ana     | 2             | 17/04/2014  |
| 1005     | Estadística         | 1        | Murray Spiegel           | 123456789         | McGraw Hill  | 3         | García  | Roca    | René    | 3             | 16/04/2014  |
| 1006     | Oracle University   | 3        | Nancy Greenberg          | 789123456         | Oracle Corp. | 4         | García  | Roque   | Luis    | 4             | 20/04/2014  |
| 1007     | Clipper 5.01        | 5        | Ramalho                  | 123456789         | McGraw Hill  | 5         | Pérez   | Gómez   | Juan    | 5             | 18/04/2014  |


---

## Ejercicio 2FN

La anterior tabla no cumple con el requisito **2NF** haz que se cumpla

### Solución 
Está tabla no cumple con el requisito **2NF** ya que tiene atributos no clave que no dependen por completo de una clave primaria, por eso dividiremos está tabla en tres una para los **Libros**, otra para los **Lectores** y otra para las **Devoluciones**.

Tabla **Libro**:

| Código | Título              | Autor             | Editorial     | TelefonoEditorial  |
|--------|---------------------|-------------------|---------------|--------------------|
| 1001   | Variable compleja   | Murray Spiegel    | McGraw Hill   | 123456789          |
| 1004   | Visual Basic 5      | E. Petroustsos    | Anaya         | 987654321          |
| 1005   | Estadística         | Murray Spiegel    | McGraw Hill   | 123456789          |
| 1006   | Oracle University   | Nancy Greenberg   | Oracle Corp   | 789123456          |
| 1007   | Clipper 5.01        | Ramalho McGraw    | McGraw Hill   | 123456789          |



Tabla **Lectores**:

| CodLector | Paterno   | Materno  | Nombres           |
|-----------|-----------|----------|-------------------|
| 1         | Pérez     | Gómez    | Juan              |
| 2         | Ríos      | Terán    | Ana               |
| 3         | Roca      | García   | René              |
| 4         | García    | Roque    | Luis              |

Tabla **Devoluciones**:

| CodLibro | CodLector | FechaDev    |
|----------|-----------|-------------|
| 1001     | 1         | 15/04/2014  |
| 1004     | 2         | 17/04/2014  |
| 1005     | 3         | 16/04/2014  |
| 1006     | 4         | 20/04/2014  |
| 1007     | 1         | 18/04/2014  |

--- 

## Ejercicio 3NF

La anterior tabla no cumple con el requisito **3NF** haz que se cumpla

### Solución
Está tabla no cumple con el requisito **3NF** ya que los atributos no clave que dependen de una columna que depende de la clave primaria. Por eso crearemos nuevas tablas y establecer relaciones entre ellas.

Tabla **Libros**: 

| Código | Título              | 
|--------|---------------------|
| 1001   | Variable compleja   |
| 1004   | Visual Basic 5      | 
| 1005   | Estadística         |
| 1006   | Oracle University   | 
| 1006   | Oracle University   | 
| 1007   | Clipper 5.01        |

Tabla **Autores**:

| CodAutor | Autor               |
|----------|---------------------|
| 1        | Murray Spiegel      |
| 2        | E. Petroustsos      |
| 3        | Nancy Greenberg     |
| 4        | Priya Nathan        |
| 6        | Ramalho             |

Tabla **Editoriales**:

| CodEditorial | Editorial     | TelefonoEditorial |
|--------------|---------------|-------------------|
| 1            | McGraw Hill   | 123456789         |
| 2            | Anaya         | 987654321         |
| 3            | Oracle Corp   | 789123456         |

Tabla **LibroEditorial**:

| CodLibro | CodEditorial |
|----------|--------------|
| 1001     | 1            |
| 1004     | 2            |
| 1005     | 1            |
| 1006     | 3            |
| 1007     | 1            |

Tabla **LibroAutor**:

| CodLibro | CodAutor |
|----------|----------|
| 1001     | 1        |
| 1004     | 2        |
| 1005     | 1        |
| 1006     | 3        |
| 1006     | 4        |
| 1007     | 6        |


Tabla **Lectores**:

| CodLector | Paterno   | Materno  | Nombres           |
|-----------|-----------|----------|-------------------|
| 1         | Pérez     | Gómez    | Juan              |
| 2         | Ríos      | Terán    | Ana               |
| 3         | Roca      | García   | René              |
| 4         | García    | Roque    | Luis              |


Tabla **Devoluciones**:

| CodDevolucion | CodLibro | CodLector | FechaDev    |
|---------------|----------|-----------|-------------|
| 1             | 1001     | 1         | 15/04/2014  |
| 2             | 1004     | 2         | 17/04/2014  |
| 3             | 1005     | 3         | 16/04/2014  |
| 4             | 1006     | 4         | 20/04/2014  |
| 5             | 1007     | 1         | 18/04/2014  |