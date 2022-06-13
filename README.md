# Movies

## Refactoring: Movies

## <em>**Versión 1.**</em> Clase “Customer” - Método “statement()”

### <em>**Smell code**</em>:
####  Método largo => más de 15 líneas
- Mal reparto de responsabilidades => Falta de Cohesión
- Imposible reutilizar para otro formato (HTML) => Inmóvil
  * copy+paste => DRY
- Cambio de política de coste y puntos => 
  * Viscoso
- copy+paste => multiplica y complica el mantenimiento

### <em>**Refactoring**</em>: 

Extraer Método => switch y código dependiente en método “amountFor” de clase Customer|

## <em>**Versión 2.**</em> Clase “Customer“ - Método “amountFor()“

### <em>**Smell code:**</em>

- Malos nombres => “each” y “thisAmount”

### <em>**Refactoring:**</em>

- Renombrar variable => “rental” y “result”

## <em>**Versión 3.**</em> Clase “Customer“ - Método “amountFor()“

### <em>**Smell Code:**</em>

- Envidia de características => get(), get(), … desde el servidor

- Clase de Datos => get(), get(), … en el cliente
Experto en Información => la clase responsable es la que tiene la información

### <em>**Refactoring**</em>

- Mover método => método “getCharge” a clase “Rental”

## <em>**Versión 4.**</em> Clase “Customer“ – Método “amountFor()“

### <em>**Smell Code:**</em>

- “Innecesaria descomposición”: método privado sin justificación

### <em>**Refactoring**</em>

- Método en línea => eliminar “amountFor”


## <em>**Versión 5.**</em> Clase “Customer“ – Método “statement()“

### <em>**Smell Code:**</em>

- Variable temporal innecesaria => “thisAmount”

### <em>**Refactoring**</em>

- Reemplazar Temporal por Consulta => “each.getCharge()”

## <em>**Versión 6.**</em> Clase “Customer“ – Método “statement()“

### <em>**Smell Code:**</em>

- Método largo => más de 15 líneas

### <em>**Refactoring**</em>

- Extraer método => método “getFrequentRenterPoints()“ a clase “Rental”

## <em>**Versión 7.**</em> Clase “Customer“ – Método “statement()“

### <em>**Smell Code:**</em>

- Variable temporal innecesaria => “totalAmount”

### <em>**Refactoring**</em>

- Reemplazar Temporal por Consulta => “this.getTotalCharge()”


## <em>**Versión 8.**</em> Clase “Customer“ – Método “statement()“

### <em>**Smell Code:**</em>

- Variable temporal innecesaria => “frequentRenterPoints”

### <em>**Refactoring**</em>

- Reemplazar Temporal por Consulta =>  “this.getTotalFrequentRenterPoints()”


## <em>**Versión 9.**</em> Clase “Rental“ – Método “getCharge()“

### <em>**Smell Code:**</em>

- Experto en la Información => la mayor parte de la información es de Movie

### <em>**Refactoring**</em>

- Mover Método => método “getCharge()” a clase “Movie”

## <em>**Versión 10.**</em> Clase “Rental“ – Método “getFrequentRenterPoints()“

### <em>**Smell Code:*</em>

- Experto en la Información => la mayor parte de la información es de Movie

### <em>**Refactoring**</em>

- Mover Método => método “getFrequentRenterPoints()” a clase “Movie”


## <em>**Versión 11.**</em> Clase “Movie“ – Método “getCharge()“

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Código de Tipo con Estrategia/Estado (inyección de dependencias) => Auto-encapsular campo => “priceCode”


## <em>**Versión 12.**</em> Clase “Movie“ – Método “getCharge()“

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Código de Tipo con Estrategia/Estado (inyección de dependencias) => Añadir nuevas clases => “Price”, “ChildrenPrice”, ...

## <em>**Versión 13.**</em> Clase “Movie” - Atributo “priceCode”

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Código de Tipo con Estrategia/Estado (inyección de dependencias) => Sustituir atributo: “int priceCode” por “Price price”


## <em>**Versión 14.**</em> Clase “Movie” - método “getCharge()”

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Código de Tipo con Estrategia/Estado (inyección de dependencias) => Mover método: método “getCharge()” a  Clase “Price”


## <em>**Versión 15.**</em> Clase “Price” - método “getCharge()”

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Condicional con Polimorfismo => Redefinir método “getCharge()” en clases derivadas


## <em>**Versión 16.**</em> Clase “Price” - método “getFrequentRenterPoints()”

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Reemplazar Condicional con Polimorfismo => Redefinir método “getFrequentRenterPoints()” en clases derivadas

## <em>**Versión 17.**</em> Clase “CustomerTest” - métodos de prueba con Tipo/Código

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Ocultar campo: añadir métodos “childrens()”, “regular()” y “newRelease()” en clase “MovieBuilder

## <em>**Versión 18.**</em> Clase “CustomerTest” - métodos de prueba con Tipo/Código

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

-	Ocultar campo: desde “CustomerTest” llamar a métodos “childrens()”, “regular()” y “newRelease()” de clase “MovieBuilder”
-	Sustituir campo: atributo “priceCode” por “Price” en clase “MovieBuilder”
-	Sustituir campo: atributo “priceCode” por “Price” en clase “Movie”

## <em>**Versión 19.**</em> Clase “Price” - método “getPriceCode()”

### <em>**Smell Code:**</em>

- Sentencia Alternativa Múltiple => el comportamiento depende de un tipo/código/...

### <em>**Refactoring**</em>

- Eliminar método: “getPriceCode()” de clases “Price” y “Movie”

## <em>**Versión 20.**</em> Jerarquía “Price”

### <em>**Smell Code:**</em>

- Números mágilos => 2, 1.5, ...

### <em>**Refactoring**</em>

- Añadir atributo: “CHARGE”, “DAYS_RENTER_THRESHOLD”, ... en jerarquía “Price”

## <em>**Versión 21**</em>
