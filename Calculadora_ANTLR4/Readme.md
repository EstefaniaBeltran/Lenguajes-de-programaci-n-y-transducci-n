# Calculadora con ANTLR4

Angel Arcos- Yeimy Beltrán - Nicolas Gutierrez - Samuel Lagos

## Descripción

En este proyecto se realizó una calculadora utilizando **ANTLR4 y Java**, tomando como base el ejemplo `LabeledExpr`.

La calculadora permite realizar operaciones básicas como suma, resta, multiplicación y división. También permite utilizar paréntesis y guardar valores en variables para utilizarlos posteriormente en otras operaciones.

## Requisitos

Para ejecutar el proyecto se debe tener instalado:

* Java
* ANTLR4
* Linux

## Estructura del proyecto

Los archivos principales utilizados son:

```text
LabeledExpr.g4
Calc.java
EvalVisitor.java
```

A partir de la gramática `LabeledExpr.g4` se generan los archivos necesarios para el funcionamiento del lexer, parser y visitor.

## Generación de archivos

El archivo `LabeledExpr.g4` contiene la gramática de la calculadora. En este archivo se definen las reglas que permiten reconocer las expresiones, números, variables, operadores, paréntesis y saltos de línea.

Una vez ubicados en la carpeta del proyecto, se utiliza el siguiente comando:

```bash
antlr4 -no-listener -visitor LabeledExpr.g4
```

La opción `-no-listener` indica que no se genere el listener, mientras que `-visitor` hace que ANTLR genere los archivos relacionados con el visitor, que son necesarios para utilizar `EvalVisitor`.

Después de ejecutar el comando, ANTLR genera automáticamente varios archivos Java a partir de la gramática:

```text
LabeledExprLexer.java
LabeledExprParser.java
LabeledExprVisitor.java
LabeledExprBaseVisitor.java
```

El `Lexer` se encarga de reconocer los diferentes elementos de entrada, mientras que el `Parser` utiliza las reglas de la gramática para analizar la estructura de las expresiones.

Los archivos `LabeledExprVisitor.java` y `LabeledExprBaseVisitor.java` permiten utilizar el patrón Visitor para recorrer y evaluar el árbol generado por el parser.

También se generan algunos archivos auxiliares como `.tokens` e `.interp`, que son creados por ANTLR durante este proceso.

Al finalizar, la carpeta del proyecto contiene tanto los archivos realizados manualmente como los archivos generados por ANTLR.

## Compilación

Después de generar los archivos, se compila el proyecto con:

```bash
javac Calc.java EvalVisitor.java LabeledExpr*.java
```

Si no aparece ningún error, la compilación se realizó correctamente y se generan los archivos `.class` correspondientes.

## Archivo de prueba

Para realizar las pruebas se utilizó el archivo `t.expr`.

Uno de los ejemplos utilizados fue:

```text
193
a = 5
b = 6
a+b*2
(1+2)*3
```

La calculadora se ejecuta utilizando:

```bash
java Calc t.expr
```

Y se obtiene:

```text
193
17
9
```

El resultado corresponde a las operaciones realizadas en el archivo de prueba.

## Pruebas adicionales

Para comprobar que las operaciones funcionaran correctamente, se agregaron otras expresiones al archivo `t.expr`:

```text
10+5
20-8
4*7
20/5
(10+2)*3
```

Resultados:

```text
15
12
28
4
36
```

También se probó el uso de variables:

```text
x = 10
y = 3
x+y
x-y
x*y
x/y
```

Resultados:

```text
13
7
30
3
```

## Ejecución del proyecto

Para ejecutar nuevamente el proyecto, los comandos principales son:

```bash
antlr4 -no-listener -visitor LabeledExpr.g4
javac Calc.java EvalVisitor.java LabeledExpr*.java
java Calc t.expr
```

## Conclusión

Con las pruebas realizadas se comprobó que la calculadora funciona correctamente para operaciones básicas, uso de paréntesis y manejo de variables mediante ANTLR4 y Java.
