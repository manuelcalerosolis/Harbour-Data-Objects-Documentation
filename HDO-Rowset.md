# HDO Documentación 

## TRowSet

Clase para la nevegacón por datos, obtenidos desde la conexión con una base de datos SQL.

## Metodos

### New()

**Sintaxis:**

TRowSet():New( <oDatabase>, <cSentence> )

**Argumentos:**

- *<oDatabase>* 

  Objeto que representa la conexión con la base de datos.

- *<cSentence>* 

  Sentencia SQL para obtener campos seleccionados, de una o mas tablas.
  
**Devuelve:**
Una referencia al objeto TRowSet recien creado.

**Descripción:**
Es el método constructor de la clase.

**Ejemplo:**
```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like 'R%'" )
```

### bindParam()

**Sintaxis:**

bindParam( <nParameter>, <variable> )

**Argumentos:**

- *<nParameter>* 

  Identificador del parámetro, posicion del parametro de sustición en el comando SQL.

- *<cSentence>* 

  Nombre de la variable de Harbour a vincular al parámetro de la sentencia SQL.

**Devuelve:**

Vedadero, en caso de éxito, falso en caso de error.

**Descripción:**

Vincula una variable de harbour a un parámetro de sustitución con el signo de interrogación correspondiente de la sentencia SQL.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:bindParam( 1, @cLast )
	oRowSet:load()
```

### bindValue()

**Sintaxis:**

bindValue( <nParameter>, <cValue> )

**Argumentos:**

- *<nParameter>* 

  Identificador del parámetro, posicion del parametro de sustición en el comando SQL.

- *<cValue>* 

  Valor a vincular al parámetro de la sentencia SQL.

**Devuelve:**

Vedadero, en caso de éxito, falso en caso de error.

**Descripción:**

Vincula un valor a un parámetro de sustitución con el signo de interrogación correspondiente de la sentencia SQL.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:bindParam( 1, "R%" )
	oRowSet:load()
```

### getQueryStr()

**Sintaxis:**

getQueryStr()

**Devuelve:**

La sentencia SQL con la que se invoco el la creación del RowSet.

**Descripción:**

Muestra la sentecia completa con la que se creo el objeto RowSet.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like R%" )
	oRowset:getQueryStr() // --> "SELECT * FROM test WHERE last like R%"
```

### bindParamCount()

**Sintaxis:**

bindParamCount()

**Devuelve:**

El número de parametros de sustitución de la sentecncia SQL del RowSet.

**Descripción:**

Muestra el número de parametros de la sentecia completa con la que se creo el objeto RowSet.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:bindParam( 1, "R%" )
	oRowSet:bindParamCount() // --> 1
```

### errorCode()

**Sintaxis:**

errorCode()

**Devuelve:**

El último código de error, en la ejecución de RowSet.

**Descripción:**

Muestra el código de error en la última ejecución de RowSet, o ceros, si no hubo errores.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:errorCode() // --> 00000
```

### errorNo()

**Sintaxis:**

errorNo()

**Devuelve:**

El último número de error, en la ejecución de RowSet.

**Descripción:**

Muestra el número de error en la última ejecución de RowSet, o cero, si no hubo errores.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:errorNo() // --> 0
```

### errorStr()

**Sintaxis:**

errorStr()

**Devuelve:**

El último texto de error, en la ejecución de RowSet.

**Descripción:**

Muestra el texto de error en la última ejecución de RowSet, o cero, si no hubo errores.

**Ejemplo:**

```xbase
	oRowset := TRowSet():new( oDataBase, "SELECT * FROM test WHERE last like ?" )
	oRowset:errorStr() // --> ""
```

