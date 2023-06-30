# curso-fundamentos-sass
Notas de clase

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

#### <em>At-rules CSS</em>
Es una declaración que cumple con diferentes funciones, se inicializa con el símbolo @ y cuenta con sintaxis propia.
Las at-rules dentro de SASS ayudan a mantener la compatibilidad con proximas versiones de CSS.
    - @use --> Nos ayuda a importar los modulos, estilos y funciones de otras hojas de estilos
    - @import --> Se encarga de importar los estilos globales
    - @function --> Nos permite crear funciones personalizadas, pero SASS cuenta con funciones ya existentes
    - @forward --> Recibe como parametro una URL y nos ayuda a cargar los estilos de nuestra hoja de estilos
    - @extend --> Tiene que ver con el concepto de herencia ******
    - @at-root --> Se encarga de cargar nuestros estilos en el root de nuestro CSS
Dentro de las reglas que tienen que ver con la compilación podemos encontrar
    - @error: error en la compilación, @warn: alerta de modificación, @debug: para encontrar los errores de una manera más sencilla
    - @include: nos ayuda a invocar los mixins
    - @for, @if, @each, @while tienen que ver con estructuras de control

#### <em>Nesting</em>
- La anidación permite tener selectores dentro de otros, lo cual nos ayuda a simplificar el código
- Escribiendo los selectores en el orden en que aparecen en el HTML

```
    nav {
        ul {
            margin: 4px;
            padding: 5px;
            list-style: none;
        }
        li {
            display: inline-block;
        }
        a {
            display: block;
            pading: 6px 12px;
            text-decoration: none;
        }
    }
```

### <em>Expresiones</em>
Una expresión es todo aquello que va del lado derecho de una variable, admitiendo varios tipos de valores.
Las expresiones son mucho más poderosas que los valores CSS simples, ya que se pasan como argumentos a mixins y funciones
#### Expresiones
    - Números
    - Strings
    - Colores
    - Booleanos
    - Null
    - Listas
    - Mapas

## <em>Herencia</em>
La herencia es un mecanismo mediante el cual un selector puede recibir estilos CSS que vienen de variables utilizadas previamente.

### <em>Uso de la herencia en SASS</em>
La directive <em>@extend</em> de SASS nos permite organizaaaa código y crear CSS más limpio
```
    .error {
        border: 1px #f00;
        background-color: #fdd;
        &--serius {
            @extend .error;
            border-wodth: 3px;
        }
    }
```

## <em>Mixins</em>
Los mixins permiten definir estilos que se pueden reutilizar en toda su hoja de estilos y facilitan evitar el uso de clases no semánticas.

### <em>Uso de mixins en SASS</em>
Se declara con la regla @mixin seguido del nombre que queremos asignar y se invoca con @include seguido del nombre del mixin.
```
    @mixin horizontal-list {
        li {
            display: inline-block;
            margin: {
                left: -2px;
                right: 2em;
            }
        }
    }

    nav ul {
        @include horizontal-list;
    }
```
### <em>Argumentos en mixins</em>
- Un argumento es el nombre de una variable que está separada por una coma.
- La utilidad de los mixins no sería tal si no tuvieran la capacidad de recibir argumentos.
```
    @mixin circle2 ($width, $height, $color) {
        width: $width;
        height: $height;
        background: $color;
    }
```

## <em>Funciones en SASS</em>
Las funciones permiten definir operaciones complejas en valores de SASS.
Las funciones se definen usando a regla @function.
SASS como preprocesador tiene una gran cantidad de funciones. Algunos de los ejemplos son:
    - Funciones RGB
    - Funciones HSL
    - Funciones de opacidad
    - Funciones sobre strings
    - Funciones sobre números
### <em>Operaciones</em>
SASS es compatible con una gran cantidad de operadores útiles para trabajar con diferentes valores. Estos incluyen los operadores matemáticos estándar y operadores para varios otros tipos, por ejemplo: == y !=.
#### <em>Jerarqu+ia de operaciones</em>
    1. Los operadores unarios not, + y -
    2. Los operadores *, / y %
    3. Los operadores + y -
    4. Los operadores >, >=, < y >=
    5. Los operadores de comparación == y !=
    6. El operadore lógico and
    7. El operadore lógico or
    8. El operador de asignación =
### <em>Declaración de una función</em>
Las funciones se llaman utilizando la sintaxis de función CSS normal
```
    @function pow($base, $exponent) {
        $result: 1;
        @for $_ from 1 through $exponent {
            $result: $result * $base;
        }
        @return $result;
    }

    .sidebar {
        float: left;
        margin-left: pow(4, 3) * 1px;
    }
```
