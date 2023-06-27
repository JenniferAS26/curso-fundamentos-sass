# Live SASS Compiler
```
    ctrl + shift + p
```

<em>Estructura de la hoja de estilos</em>
Algunos statements contienen bloques y se definen entre laves {}, son separados por punto y coma ;

<em>Declaraciones</em>: Solo se pueden usar en la parte superior de la hoja, también son llamadas 
Top-Level Statemens
    - Imports
    - Definición de un Mixin
    - Definición de una función
    - Modulos

<em>Universal Statemens</em>
- Variables, estructuras de control y las reglas @error, @warn y @debug
- Declaraciones CSS: Reglas de estilos, At-rules, mixins

<em>Variables</em>
Una variable es un espacio asignado en memoria y únicamente puede almacenar un dato
    - Las variables pueden ser declaradas en cualquier parte de la hoja de estilos

<em>Declaración de variables</em>
Para asignar un valor se hace uso del simbolo $ de esta manera es posible referenciar dentro de la hoja de estilos

```
    $primary-color: blue;
    $secondary-color: green;
    $tertiary-color: purple;

```

<em>CSS Varibles</em>
    - Pueden tener diferentes valores para distintos elementos
    - Son declarativas
<em>SASS Varibles</em>
    - Tienen un valor único correspondiente a un elemento
    - Son imperativas

<em>!default flag</em>
Se encarga de asignar un valor a la variable si y solo si esta variable no está definida o su valor es null.

## Uso de selectores, scope de las variables y shadowing
<em>Selectores</em>
Un selector de CSS define sobre qué elementos se aplicará un confunto de reglas CSS.
Ecisten selectores de tipo:
    - Clase
    - Id
    - Tipo
    - Atributo

<em>¿Qué es el Scope?</em>
