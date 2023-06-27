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

<em>CSS Variables</em>
    - Pueden tener diferentes valores para distintos elementos
    - Son declarativas
<em>SASS Variables</em>
    - Tienen un valor único correspondiente a un elemento
    - Son imperativas

<em>!default flag:</em>
Se encarga de asignar un valor a la variable si y solo si esta variable no está definida o su valor es null.

## Uso de selectores, scope de las variables y shadowing
<em>Selectores</em>
Un selector de CSS define sobre qué elementos se aplicará un confunto de reglas CSS.
Ecisten selectores de tipo:
    - Clase
    - Id
    - Tipo
    - Atributo

### <em>¿Qué es el Scope?</em>
El scope dentro de SASS hace referecia al contexto en el que son declaradas las variables donde es posible hacer uso de las mismas
#### <em>Variables locales</em>
- Las variables locales estan declaradas dentro de un bloque {}
- Cualquier selector anidado puede acceder a las variables locales declaradas dentro del selector

#### <em>Variables globales</em>
Por defecto, todas las variables declarads fuera de un selector son variables globales, esto significa que podemos acceder a ellas en cualquier parte de nuestra hoja de estilos.

#### <em>Shadowing</em>
Las variables locales y globales pueden tener los mismo nombres ya que se encuentran en diferente nivel de scope.
Esto puede ayudar a que no se llegue a modificar por error el valor de las variables globales.
