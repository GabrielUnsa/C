# C — Ejercicios y proyectos de programación

Colección de ejercicios académicos en C sobre programación estructurada, registros, tipos abstractos de datos (TAD), listas, recursión, comunicación entre procesos con MPI y análisis léxico y sintáctico.

El repositorio reúne programas independientes y proyectos modulares. Cada ejemplo tiene sus propios archivos de entrada y dependencias; se compila por separado.

Estos ejercicios prácticos fueron realizados durante el cursado de diversas materias mientras estudiaba la **Licenciatura en Análisis de Sistemas (Plan 2010)** de la **Universidad Nacional de Salta**.

**Materia: Introduccion a la programacion, Teoria de la Computacion I & II**

## Contenido

- [Estructura del repositorio](#estructura-del-repositorio)
- [Introducción a la Programacion con C](#introducción-a-la-programacion-con-c)
- [Proyecto Transversal](#proyecto-transversal)
- [Compilación y ejecución](#compilación-y-ejecución)
- [Estado y compatibilidad](#estado-y-compatibilidad)
- [Licencia](#licencia)

## Estructura del repositorio

```text
.
├── Introduction to C/
│   ├── Programas Simples en C/   # Fundamentos, registros, agendas y MPI
│   ├── Ejemplos_TAD/             # Módulos de alumnos y listas de datos
│   │   ├── TAD_alumno/
│   │   ├── TAD_lista_datos/
│   │   ├── usa_alu/
│   │   └── usa_lista/
│   ├── ListaEnlazadaRec/         # Nodos y operaciones recursivas
│   └── RecurcionTAD/             # Recursión, ordenamiento y búsqueda
├── Transversal/
│   ├── Grammar.txt              # Propuesta de gramática de conjuntos
│   ├── Proyecto/
│   │   ├── Cap4.c               # Analizador léxico de expresiones
│   │   ├── parser.c             # Borrador de analizador sintáctico
│   │   └── Transversal/         # Analizador modular y entrada de ejemplo
│   └── README.md
├── LICENSE
└── README.md
```

## Introducción a la Programacion con C

### Programas simples

La carpeta [Programas Simples en C](Introduction%20to%20C/Programas%20Simples%20en%20C/) contiene ejercicios de consola, desde operaciones básicas hasta estructuras compuestas y comunicación distribuida.

| Archivo | Descripción |
| --- | --- |
| `Introduccion a librerias.c` | Uso de `stdio.h`, variables, una operación aritmética y salida con `printf`. Incluye comentarios sobre ciclos y condicionales. |
| `Introduccion Ingreso de Valores.c` | Carga de datos de alumnos, cálculo de edades, conteo por rangos de edad y estatura, y selección por estatura. Utiliza 2018 como año de referencia. |
| `introduccion a registros.c` | Carga y visualización de una estructura con un entero y un real; modificación de sus campos mediante un puntero. |
| `persona.c` | Registro de nombre, DNI y edad; paso de estructuras por valor y por referencia. |
| `ejemplo_lis_reg.c` | Agenda de personas con fecha de nacimiento y contacto representado mediante una unión; carga mediante punteros. |
| `agenda.c` | Carga y visualización de una agenda, con una función propia para leer cadenas. |
| `nPersonas.c` | Variante de agenda con estructuras anidadas y unión para teléfono o correo. Los comentarios proponen extensiones de cumpleaños, edición y regalos que aún no están implementadas. |
| `TP4-C2.c` | Registro de atletas y visualización de quienes alcanzan la mayor cantidad de medallas. |
| `Ej8Bloq.c` | Intercambio de vectores entre procesos organizados en anillo mediante operaciones bloqueantes de MPI. |
| `Ej8NoBloq.c` | Variante con operaciones no bloqueantes de MPI y esperas mediante `MPI_Wait`. |
| `union.c` | Ejecuta las variantes no bloqueante y bloqueante del intercambio en anillo e imprime sus mediciones de tiempo. |

### Tipos abstractos de datos

Los proyectos de [Ejemplos_TAD](Introduction%20to%20C/Ejemplos_TAD/) separan las interfaces (`.h`), las implementaciones (`.c`) y los programas que las utilizan.

| Proyecto | Propósito y archivos principales |
| --- | --- |
| [TAD_alumno](Introduction%20to%20C/Ejemplos_TAD/TAD_alumno/) | Define un alumno con nombre, DNI y edad. `TAD_alumno.c` implementa la carga, visualización y consulta del DNI; `principal.c` compara tres alumnos y muestra el de mayor DNI. |
| [usa_alu](Introduction%20to%20C/Ejemplos_TAD/usa_alu/) | Reutiliza el TAD de alumno para comparar una cantidad ingresada por teclado. La implementación se encuentra en `../TAD_alumno/TAD_alumno.c`. |
| [TAD_lista_datos](Introduction%20to%20C/Ejemplos_TAD/TAD_lista_datos/) | Define datos como pares de valores reales y una lista sobre un arreglo. Incluye carga, visualización y ordenamiento por inserción según la primera componente. Su programa principal carga y muestra la lista. |
| [usa_lista](Introduction%20to%20C/Ejemplos_TAD/usa_lista/) | Carga una lista, la muestra, la ordena y vuelve a mostrarla. Utiliza las implementaciones de `TAD_dato.c` y `TAD_lista.c` de `../TAD_lista_datos/`. |

Los archivos `.zpr` conservan las configuraciones de ZinjaI, incluidas referencias a las bibliotecas de alumnos y listas (`alu` y `lista`). Algunas rutas corresponden al entorno original de Windows y requieren ajustes para usarlas en otro equipo.

### Listas enlazadas y recursión

[ListaEnlazadaRec](Introduction%20to%20C/ListaEnlazadaRec/) organiza el código en dos módulos:

- `tad_elementos.h` y `tad_elementos.c`: un elemento compuesto por un número y una cadena, con funciones de carga y consulta.
- `tad_lista.h` y `tad_lista.c`: nodos con enlaces anterior y siguiente, inserción al final, carga y recorrido recursivos, y rutinas de eliminación por número.

El programa de demostración es `prog_principal.c`: crea dos nodos independientes y los muestra. El bloque que carga una lista y ofrece un menú de eliminación está comentado. `main.cpp` es una plantilla vacía y el proyecto `.zpr` apunta a ella; para compilar la demostración en C se deben seleccionar los archivos indicados más abajo.

[RecurcionTAD](Introduction%20to%20C/RecurcionTAD/) contiene un TAD de lista sobre un arreglo de enteros. `lista.c` implementa carga pseudoaleatoria recursiva, visualización en orden inverso, suma, ordenamiento rápido (*quicksort*) y búsqueda binaria recursiva. `ppal.c` utiliza esas operaciones y genera también el valor que se busca. `sin_titulo.c` es un ejercicio independiente de llamadas recursivas y conteo.

## Proyecto Transversal

[Transversal](Transversal/) reúne material de Teoría de la Computación II sobre gramáticas y analizadores.

### Gramática de conjuntos

[Grammar.txt](Transversal/Grammar.txt) propone un lenguaje en EBNF con un bloque principal `fun Principal`, asignaciones, conjuntos de números y sentencias de impresión. Define las siguientes operaciones:

| Símbolo | Operación propuesta |
| --- | --- |
| `+` | Unión |
| `-` | Diferencia |
| `/` | Intersección |
| `==` | Igualdad |
| `$` | Pertenencia |

Esta gramática es una especificación de referencia. Los analizadores en C incluidos trabajan con expresiones y fragmentos de sintaxis de C; el repositorio no contiene una implementación completa del lenguaje de conjuntos.

### Analizadores incluidos

| Archivo o grupo | Descripción |
| --- | --- |
| `Proyecto/Cap4.c` | Analizador léxico de identificadores, enteros, paréntesis y operadores aritméticos. Intenta abrir `front.in`, archivo que no está incluido. |
| `Proyecto/parser.c` | Borrador de analizador sintáctico con funciones para tipos, punteros, parámetros y bloques. Contiene errores de sintaxis y referencia un `parser.h` ausente. |
| `Proyecto/Transversal/Lexic.c` y `Lexic.h` | Analizador léxico modular de identificadores, palabras de almacenamiento, tipos y signos de puntuación. |
| `Proyecto/Transversal/Pars.c` y `Pars.h` | Analizador sintáctico con funciones para reconocer la estructura de una función, sus parámetros y un bloque sencillo. |
| `Proyecto/Transversal/Test.c` | Programa principal que conecta ambos analizadores y muestra el recorrido del análisis. |
| `Proyecto/Transversal/Lexico.c` | Variante del analizador léxico; el proyecto `EJERCICIO2.zpr` selecciona `Lexic.c`. |
| `Proyecto/Transversal/EJERC1.in.txt` | Entrada de ejemplo: `int fibonacci (int x){ salta;}`. Es texto para analizar, no una implementación de Fibonacci. |

El README de esta subcarpeta menciona Flex y Bison, pero no se incluyen especificaciones `.l` o `.y` ni un proceso de generación con esas herramientas. Los archivos disponibles muestran analizadores escritos directamente en C.

La versión modular requiere ajustes antes de compilarla con compiladores actuales: comparte variables globales definidas en varios archivos y utiliza funciones sin todas las declaraciones necesarias. Además, `Test.c` abre `EJERC1.in`, mientras que la entrada disponible se llama `EJERC1.in.txt`; es necesario hacer coincidir ambos nombres y ejecutar desde la carpeta de la entrada.

## Compilación y ejecución

### Requisitos y preparación

- Un compilador de C, como GCC, para los ejemplos en C.
- Una implementación de MPI que proporcione `mpi.h`, `mpicc` y `mpirun` para los tres ejercicios de comunicación entre procesos.
- ZinjaI, opcional, para abrir los proyectos `.zpr` existentes.

Para obtener el repositorio:

```bash
git clone https://github.com/GabrielUnsa/C.git
cd C
mkdir -p build
```

Los siguientes comandos usan una terminal Bash y se ejecutan desde la raíz del repositorio `C`. Las comillas son necesarias porque varias rutas contienen espacios. Cada comando de compilación produce un ejecutable independiente en `build/`.

### Primer programa

```bash
gcc -std=c99 -Wall -Wextra \
  "Introduction to C/Programas Simples en C/Introduccion a librerias.c" \
  -o build/introduccion
./build/introduccion
```

El programa imprime `6`.

### Estructuras y punteros

```bash
gcc -std=c99 -Wall -Wextra \
  "Introduction to C/Programas Simples en C/introduccion a registros.c" \
  -o build/registros
./build/registros
```

Solicita un entero y un real, muestra los valores originales y los vuelve a mostrar después de sumar `3` a cada campo. Por ejemplo, las entradas `2` y `1.5` producen los valores modificados `5` y `4.5`.

### Demostración de nodos

```bash
gcc -std=c99 -Wall -Wextra \
  "Introduction to C/ListaEnlazadaRec/prog_principal.c" \
  "Introduction to C/ListaEnlazadaRec/tad_lista.c" \
  "Introduction to C/ListaEnlazadaRec/tad_elementos.c" \
  -o build/lista_enlazada
./build/lista_enlazada
```

Estos tres comandos de compilación se verificaron con GCC 14.2.0 en Linux. Los ejemplos de introducción y registros también se ejecutaron; la demostración de nodos se verificó solo mediante compilación. Hay advertencias por parámetros o variables sin uso en algunos archivos.

### Ejercicios MPI

Con MPI instalado, la forma de compilar y ejecutar la variante bloqueante es:

```bash
mpicc -std=c99 -Wall -Wextra \
  "Introduction to C/Programas Simples en C/Ej8Bloq.c" \
  -o build/mpi_bloqueante
mpirun -np 4 ./build/mpi_bloqueante 10
```

`-np 4` indica la cantidad de procesos y `10` es el tamaño del vector que el programa obtiene de `argv[1]`. Para las otras variantes, se cambia el archivo fuente por `Ej8NoBloq.c` o `union.c` y se elige otro nombre de ejecutable.

Este ejemplo de uso de MPI no fue verificado en el entorno de documentación, donde MPI no estaba instalado. Los programas requieren revisión antes de interpretar sus resultados: el acumulador `X` se utiliza sin inicialización y las mediciones con `clock()` necesitan evaluarse según lo que se quiera comparar.

## Estado y compatibilidad

El código conserva ejercicios y versiones de trabajo con fines de estudio. No hay un sistema de compilación común ni una suite de pruebas automatizadas incluida.

- Algunos programas usan `gets`, retirada del estándar desde C11, o `fflush(stdin)`, cuyo comportamiento no está definido por el estándar de C. La lectura de cadenas requiere adaptación para un uso portable.
- Hay arreglos recorridos desde el índice `1`, tamaños ingresados sin validación y variables sin inicializar. Conviene revisar los límites y la entrada antes de ampliar los ejemplos.
- `RecurcionTAD/lista.c` llama a funciones antes de declararlas y `TAD_lista_datos/TAD_dato.c` utiliza entrada y salida sin incluir `stdio.h`; los compiladores actuales pueden rechazar estos archivos.
- Las rutinas de eliminación de `ListaEnlazadaRec` requieren revisión del mantenimiento de enlaces y de los casos de lista vacía antes de activar el menú comentado.
- `Introduccion Ingreso de Valores.c` conserva una llamada a `system("cls")`, propia del entorno de consola de Windows.
- Cada programa tiene su propio punto de entrada. Para los proyectos modulares hay que enlazar el programa principal con sus implementaciones; compilar todos los archivos del repositorio juntos produce conflictos entre funciones `main` y otros símbolos.

Para explorar el material, se puede comenzar por los programas simples, continuar con los TAD y las listas, y luego revisar recursión, MPI y analizadores.

## Licencia

Distribuido bajo la [licencia MIT](LICENSE). Copyright © 2025 Gabriel Marmanillo.
