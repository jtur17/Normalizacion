# Normalización

## Ejercicio 1FN

| **CodLibro** | **Titulo**               | **Autor**                           | **Editorial**    | **NombreLector**            | **echaDev** |
|--------------|--------------------------|-------------------------------------|------------------|-----------------------------|-------------|
| 1001         | Variable Compleja        | Murray Spiegel                      | McGraw Hill      | Pérez Gómez, Juan           | 15/04/2014  |
| 1004         | Visual Basic             | E. Petroustsos                      | Anaya            | Ríos Terán, Ana             | 17/04/2014  |
| 1005         | Estadística              | Murray Spiegel                      | McGraw Hill      | Roca García René            | 16/04/2014  |
| 1006         | Oracle University        | Nancy Greenberg y PriyaNathan       | Oracle Corp.     | García Roque, Luis          | 20/04/2014  |
| 1007         | Clipper 5.01             | Ramalho                             | McGraw Hill      | Pérez Gómez, Juan           | 18/04/2014  |



### Solución

Esta tabla no cumple el requisito **1NF** de sólo tener campos atómicos, ya que el nombre del lector es un campo en el que se puede dividir en dos columnas más, en primer apellido y segundo apellido, tal como lo muestra la siguiente tabla.


| CodLibro | Titulo              | Autor                    | Editorial    | Paterno | Materno | Nombres | FechaDev    |
|----------|---------------------|--------------------------|--------------|---------|---------|---------|-------------|
| 1001     | Variable compleja   | Murray Spiegel           | McGraw Hill  | Pérez   | Gómez   | Juan    | 15/04/2014  |
| 1004     | Visual Basic 5      | E. Petroustsos           | Anaya        | Ríos    | Terán   | Ana     | 17/04/2014  |
| 1005     | Estadística         | Murray Spiegel           | McGraw Hill  | García  | Roca    | René    | 16/04/2014  |
| 1006     | Oracle University   | NancyGreenberg           | Oracle Corp. | García  | Roque   | Luis    | 20/04/2014  |
| 1006     | Oracle University   | Priya Nathan             | Oracle Corp. | García  | Roque   | Luis    | 20/04/2014  |
| 1007     | Clipper 5.01        | Ramalho                  | McGraw Hill  | Pérez   | Gómez   | Juan    | 18/04/2014  |


---

## Ejercicio 2FN

La anterior tabla no cumple con el requisito **2NF** haz que se cumpla

### Solución 
Está tabla no cumple con el requisito **2NF** ya que tiene atributos no clave que no dependen por completo de una clave primaria, por eso dividiremos está tabla en tres una para los **Libros**, otra para los **Lectores** y otra para las **Devoluciones**.

Tabla **Libro**:

| Código | Título              | Autor             | Editorial     |
|--------|---------------------|-------------------|---------------|
| 1001   | Variable compleja   | Murray Spiegel    | McGraw Hill   |
| 1004   | Visual Basic 5      | E. Petroustsos    | Anaya         |
| 1005   | Estadística         | Murray Spiegel    | McGraw Hill   |
| 1006   | Oracle University   | Nancy Greenberg   | Oracle Corp   |
| 1006   | Oracle University   | Priya Nathan      | Oracle Corp   |
| 1007   | Clipper 5.01        | Ramalho McGraw    | McGraw Hill   |


Tabla **Lectores**:

| CodLector | Paterno   | Materno  | Nombres           |
|-----------|-----------|----------|-------------------|
| 501       | Pérez     | Gómez    | Juan              |
| 502       | Ríos      | Terán    | Ana               |
| 503       | Roca      | García   | René              |
| 504       | García    | Roque    | Luis              |

Tabla **Devoluciones**:

| CodLibro | CodLector | FechaDev    |
|----------|-----------|-------------|
| 1001     | 501       | 15/04/2014  |
| 1004     | 502       | 17/04/2014  |
| 1005     | 503       | 16/04/2014  |
| 1006     | 504       | 20/04/2014  |
| 1007     | 501       | 18/04/2014  |

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
| 801      | Murray Spiegel      |
| 802      | E. Petroustsos      |
| 803      | Nancy Greenberg     |
| 804      | Priya Nathan        |
| 806      | Ramalho             |

Tabla **Editoriales**:

| CodEditorial | Editorial     |
|--------------|---------------|
| 901          | McGraw Hill   |
| 902          | Anaya         |
| 903          | Oracle Corp   |

Tabla **LibroEditorial**:

| CodLibro | codEditorial |
|----------|--------------|
| 1001     | 901          |
| 1004     | 902          |
| 1005     | 901          |
| 1006     | 903          |
| 1007     | 901          |

Tabla **LibroAutor**:

| CodLibro | codAutor |
|----------|----------|
| 1001     | 801      |
| 1004     | 802      |
| 1005     | 801      |
| 1006     | 803      |
| 1006     | 804      |
| 1007     | 806      |


Tabla **Lectores**:

| CodLector | Paterno   | Materno  | Nombres           |
|-----------|-----------|----------|-------------------|
| 501       | Pérez     | Gómez    | Juan              |
| 502       | Ríos      | Terán    | Ana               |
| 503       | Roca      | García   | René              |
| 504       | García    | Roque    | Luis              |


Tabla **Devoluciones**:

| CodLibro | CodLector | FechaDev    |
|----------|-----------|-------------|
| 1001     | 501       | 15/04/2014  |
| 1004     | 502       | 17/04/2014  |
| 1005     | 503       | 16/04/2014  |
| 1006     | 504       | 20/04/2014  |
| 1007     | 501       | 18/04/2014  |