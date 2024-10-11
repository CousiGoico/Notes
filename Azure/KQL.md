# Kusto Query Language

## Indice

1. [¿Qué es KQL?](#KQL)
2. [Instrucciones de consulta de usuario](#UserInstructions)
3. [Operaciones comunes](#CommonOperators)
4. [Operaciones de agregación](#AgregateOperators)
5. [Operaciones de condición](#ConditionOperators)
6. [Operaciones de unión](#UnionOperators)
7. [Visualizaciones geoespaciales](#GeospacialView)

### ¿Qué es KQL? <a id="KQL" href="#KQL" class="anchor"></a>

Kusto Query Language (KQL) es un lenguaje, usado principalmente dentro de Azure, que se suele utilizar para consultar telemetría, métricas y registros con una compatibilidad profunda con la búsqueda y el análisis de texto, operadores y funciones de series temporales, análisis y agregación, geoespaciales, búsquedas de similitud vectorial y muchas otras construcciones de lenguaje que proporcionan el lenguaje más óptimo para el análisis de datos. Permite explorar los datos y descubrir patrones, identificar anomalías y valores atípicos, crear modelos estadísticos, ... Es un lenguaje sencillo pero eficaz para consultar datos estructurados, semiestructurados y no estructurados. Es expresivo, fácil de leer y comprender la intención de la consulta, y está optimizado para las experiencias de creación. La consulta utiliza entidades de esquema que se organizan en una jerarquía similar a SQL.

#### ¿Qué es una consulta de Kusto?

Una consulta de Kusto es una solicitud de solo lectura para procesar datos y devolver resultados. La solicitud se expresa en texto sin formato, utilizando un modelo de flujo de datos que es fácil de leer, crear y automatizar. Las consultas de Kusto se componen de una o varias instrucciones de consulta.

### Instrucciones de consulta de usuario <a id="UserInstructions" href="#UserInstructions" class="anchor"></a>

#### Expresión tabular

Esta instrucción suele aparecer en último lugar en la lista de instrucciones, y tanto su entrada como su salida constan de tablas o conjuntos de datos tabulares. Dos instrucciones cualesquiera deben estar separadas por un punto y coma.

- Sintaxis: 
    Source **|** Operator1 **|** Operator2 **|** RenderInstruction

- Parámetros: 

    - Source: fuente de datos tabular.
    - Operator: operadores de datos tabulares, como filtros y proyecciones.
    - RenderInstruction: representación de operadores o instrucciones..
    

- Ejemplos:

        StormEvents 
        | where State == "FLORIDA"
        | count

#### Let

Una instrucción [let](https://learn.microsoft.com/es-es/kusto/query/let-statement?view=microsoft-fabric) define un enlace entre un nombre y una expresión. 

- Sintaxis: 
    **let** Name **=** Expression
    **let** Name **=** [view]([Parameters]) { FunctionBody }

- Parámetros: 

    - Name: nombre de la variable de tipo texto. 
    - Expression: expresión con un resultado escalar o tabular. 
    - Parameters: parámetros de la función.
    - FunctionBody: cuerpo de la función.

- Ejemplos:

        let place = "Madrid";
        let cutoff = ago(62d); 

        let sum = (value1, value2) { value1 + value2 }

#### Set

Una instrucción [set](https://learn.microsoft.com/es-es/kusto/query/set-statement?view=microsoft-fabric) se utiliza para establecer una [propiedad de solicitud](https://learn.microsoft.com/es-es/kusto/api/rest/request-properties?view=microsoft-fabric) durante la duración de la consulta. En una consulta puede haber más de una instrucción set. 

- Sintaxis: 
    **set** OptionName [**=** OptionValue]

- Parámetros: 

    - OptionName: nombre de la propiedad de solicitud.
    - OptionValue: Valor de la propiedad de solicitud.

- Ejemplos:

        set querytrace;

### Operadores comunes <a id="CommonOperators" href="#CommonOperators" class="anchor"></a>

#### Count

Se usa para encontrar el número de registros en la tabla.

- Sintaxis: 
    | **count**

- Ejemplos:

        StormEvents 
        | count

#### Take

Se usa para obtener un número determinado de registros.

- Sintaxis: 
    | **take** num

- Parámetros:

    - num: número determinado de registros que se desea obtener.

- Ejemplos:

        StormEvents 
        | take 4

#### Project

Se usa para seleccionar un subconjunto específico de columnas.

- Sintaxis: 
    | **project** [column_name]

- Parámetros:

    - [column_name]: lista de los nombres de las columnas que deseas obtener.

- Ejemplos:

        StormEvents
        | take 5
        | project State, EventType, DamageProperty


#### Distinct

Se usa para obtener los diferentes valores de una columna.

- Sintaxis: 
    | **distinct** column_name

- Parámetros:

    - column_name: nombre de la columna de la que deseas que no se repitan los valores.

- Ejemplos:

        StormEvents
        | distinct EventType

#### Where

Se usa para realizar filtros en la consulta.

- Sintaxis: 
    | **where** filter

- Parámetros:

    - filter: criterio por el que realizar el filtro de datos.

- Ejemplos:

        StormEvents
        | where State == 'TEXAS' and EventType == 'Flood'

#### sort by

Se usa para ordenar los datos por una lista de columnas.

- Sintaxis: 
    | **sort by** [column_name {asc|desc}]

- Parámetros:

    - column_name: nombre de la columna por la que se desea ordenar.
    - asc|desc: orden ascendente o descendente por el que se desea ordenar.

- Ejemplos:

        StormEvents
        | where State == 'TEXAS' and EventType == 'Flood'
        | sort by DamageProperty asc

#### top

Se usa para obtener las primeras n filas ordenadas por la columna indicada.

- Sintaxis: 
    | **top** num_reg **by** column_name {asc|desc}

- Parámetros:

    - num_reg: número de registros que se desea obtener.
    - column_name: nombre de la columna por la que se desea ordenar.
    - asc|desc: orden ascendente o descendente por el que se desea ordenar.

- Ejemplos:

        StormEvents
        | where State == 'TEXAS' and EventType == 'Flood'
        | top 5 by DamageProperty
        | project StartTime, EndTime, State, EventType, DamageProperty

#### columnas calculadas

Los operadores **project**y **extend** pueden crear columnas calculadas.

- Sintaxis: 
    | **project** column_name = expression

- Parámetros:

    - column_name: nombre de la columna que se desea dar a la columna calculada.
    - expression: expresión o calculo de valor.

- Ejemplos:

        StormEvents
        | where State == 'TEXAS' and EventType == 'Flood'
        | top 5 by DamageProperty desc
        | project Duration = EndTime - StartTime

### Operadores de agregación <a id="AgregateOperators" href="#AgregateOperators" class="anchor"></a>

#### summarize

El operador **summarize** realiza agrupaciones de las filas en función de la clausula. Similar a un group by en SQL.

- Sintaxis: 
    | **summarize** common_operator **by** column_name

- Parámetros:

    - common_operator: operador común como los anteriormente mencionados.
    - column_name: nombre de la columna que se desea dar a la columna calculada.

- Ejemplos:

        StormEvents
        | summarize TotalStorms = count() by State

#### render

El operador **render** permite renderizar el resultado en un gráfico o diagrama.

- Sintaxis: 
    | **render** graphic_type

- Parámetros:

    - graphic_type: nombre del gráfico o diagrama que representará el resultado.

- Ejemplos:

        StormEvents
        | summarize TotalStorms = count() by State
        | render barchart

#### countif

El operador **countif()** permite contar las filas en función de una condición específica.

- Sintaxis: 
    | **countif(expression)** 

- Parámetros:

    - expression: expresión que hará se cuente dicho registro.

- Ejemplos:

        StormEvents
        | summarize StormsWithCropDamage = countif(DamageCrops > 0) by State
        | top 5 by StormsWithCropDamage

#### bin

El operador **bin()** permite agregar valores númericos o de tiempo y utilizarlos como un intervalo.

- Sintaxis: 
    | **bin(column_name, format)** 

- Parámetros:

    - column_name: nombre de la columna.
    - format: formato que dará lugar al intervalo.

- Ejemplos:

        StormEvents
        | where StartTime between (datetime(2007-01-01) .. datetime(2007-12-31)) 
            and DamageCrops > 0
        | summarize EventCount = count() by bin(StartTime, 7d)

#### max, min, average

Los operadores **min()**, **max()** y **averga()** permite calcular el valor mínimo, máximo y media de una columna.

- Sintaxis: 
    | **min(column_name)** 
    | **max(column_name)** 
    | **averge(column_name)** 

- Parámetros:

    - column_name: nombre de la columna.

- Ejemplos:

        StormEvents
        | where DamageCrops > 0
        | summarize
            MaxCropDamage=max(DamageCrops), 
            MinCropDamage=min(DamageCrops), 
            AvgCropDamage=avg(DamageCrops)
            by EventType
        | sort by AvgCropDamage

#### sum

El operador **sum()** permite calcular la suma de los valores de una columna.

- Sintaxis: 
    | **sum(column_name)** 
    
- Parámetros:

    - column_name: nombre de la columna.

- Ejemplos:

        StormEvents
        | where StartTime between (datetime(2007-01-01) .. datetime(2007-12-31)) 
            and DamageCrops > 0
        | summarize CropDamage = sum(DamageCrops) by bin(StartTime, 7d)
        | render timechart

#### round

El operador **round()** permite redondear un valor numérico.

- Sintaxis: 
    | **round(column_name, num_decimals)** 
    
- Parámetros:

    - column_name: nombre de la columna.
    - num_decimals: número de decimales del redondeo.

- Ejemplos:

        StormEvents
        | summarize 
            TotalStormsInState = count(),
            StormsWithCropDamage = countif(DamageCrops > 0)
            by State
        | extend PercentWithCropDamage = 
            round((todouble(StormsWithCropDamage) / TotalStormsInState * 100), 2)
        | sort by StormsWithCropDamage




### Operadores de condición <a id="ConditionOperators" href="#ConditionOperators" class="anchor"></a>

#### iff

El operador **iff()** permite establecer una condición para una columna calculada.

- Sintaxis: 
    | **if(condition, value_if_true, value_if_false)** 
    
- Parámetros:

    - condition: condición a realizar.
    - value_if_true: valor si el resultado de la condición es verdadera.
    - value_if_false: valor si el resultado de la condición es falsa.

- Ejemplos:

        let windowStart = datetime(2007-07-01);
        let windowEnd = windowStart + 13d;
        StormEvents
        | where EventType in ("Tornado", "Flood", "Wildfire") 
        | extend bin = bin_at(startofday(StartTime), 1d, windowStart) // 1
        | extend endRange = iff(bin + 7d > windowEnd, windowEnd, 
                            iff(bin + 7d - 1d < windowStart, windowStart, 
                                iff(bin + 7d - 1d < bin, bin, bin + 7d - 1d))) // 2
        | extend range = range(bin, endRange, 1d) // 3
        | mv-expand range to typeof(datetime) // 4
        | summarize min(DamageProperty), max(DamageProperty), round(avg(DamageProperty)) by Timestamp=bin_at(range, 1d, windowStart), EventType // 5
        | where Timestamp >= windowStart + 7d; // 6

#### case

El operador **case()** permite devolver la expresión de resultado correspondiente al primer predicado satisfecho.

- Sintaxis: 
    | **case([predicate1, value_if_true], case_else)** 
    
- Parámetros:

    - predicate1: primer predicado a comprobar.
    - value_if_true: valor si el valor coincide con el primer predicado.
    - case_else: sino se cumple ningún predicado, devolverá este valor.

- Ejemplos:

        StormEvents
        | summarize InjuriesCount = sum(InjuriesDirect) by State
        | extend InjuriesBucket = case (
                                    InjuriesCount > 50,
                                    "Large",
                                    InjuriesCount > 10,
                                    "Medium",
                                    InjuriesCount > 0,
                                    "Small",
                                    "No injuries"
                                )
        | sort by State asc




#### Operadores de unión <a id="UnionOperators" href="#UnionOperators" class="anchor"></a>

#### join

El operador **join** permite realizar consultas uniendo varias tablas.

- Sintaxis: 
    | **join** kind={innerunique|inner|leftouter|rightouter|fullouter|leftsemi|leftanti|anti|leftantisemi|rightsemi|rightanti|rightantisemi} column_name on table_name
    
- Parámetros:

    - innerunique|inner|leftouter|rightouter|fullouter|leftsemi|leftanti|anti|leftantisemi|rightsemi|rightanti|rightantisemi: tipo de unión. [Ejemplos](https://learn.microsoft.com/gl-es/kusto/query/tutorials/join-data-from-multiple-tables?view=azure-data-explorer)
    - column_name: nombre de la columna.
    - table_name: nombre de la tabla a unir.

- Ejemplos:

        StormEvents
        | summarize PropertyDamage = sum(DamageProperty) by State
        | join kind=innerunique PopulationData on State
        | project State, PropertyDamagePerCapita = PropertyDamage / Population
        | sort by PropertyDamagePerCapita

#### lookup

El operador **lookup** optimiza el rendimiento de las consultas en las que una tabla de hechos se enriquece con datos de una tabla de dimensiones. Para obtener el mejor rendimiento, el sistema asume de forma predeterminada que la tabla de la izquierda es la tabla de hechos más grande y la tabla de la derecha es la tabla de dimensiones más pequeñas. Es lo contrario de la suposición que usa el operador **join**.

- Sintaxis: 
    | **lookup** left_table on right_table
    
- Parámetros:

    - left_table: nombre de la tabla grande.
    - right_table: nombre de la tabla pequeña.
    
- Ejemplos:

        SalesFact
        | lookup Products on ProductKey
        | summarize TotalSales = count() by ProductCategoryName
        | order by TotalSales desc

#### Join

Las combinaciones también se pueden realizar en función de los resultados de la consulta de la misma tabla.

- Sintaxis: 
    | **join** kind={innerunique|inner|leftouter|rightouter|fullouter|leftsemi|leftanti|anti|leftantisemi|rightsemi|rightanti|rightantisemi} (subquery)
    
- Parámetros:

    - subquery: subconsulta a unir.
    
- Ejemplos:

        StormEvents
        | where EventType == "Lightning"
        | distinct State
        | join kind=inner (
            StormEvents 
            | where EventType == "Avalanche"
            | distinct State
            )
            on State
        | project State




#### Visualizaciones geoespaciales <a id="GeospacialView" href="#GeospacialView" class="anchor"></a>

#### Trazar puntos en un mapa

        StormEvents
        | take 100
        | project BeginLon, BeginLat
        | render scatterchart with (kind = map)

#### Trazar varias series de puntos

        StormEvents
        | take 100
        | project BeginLon, BeginLat, EventType
        | render scatterchart with (kind = map)

#### Usar valores GeoJSON para trazar puntos en un mapa

        StormEvents
        | project BeginLon, BeginLat
        | summarize by hash=geo_point_to_s2cell(BeginLon, BeginLat, 5)
        | project point = geo_s2cell_to_central_point(hash)
        | project lng = toreal(point.coordinates[0]), lat = toreal(point.coordinates[1])
        | render scatterchart with (kind = map)

#### Representar puntos de datos con burbujas de tamaño variable

        StormEvents
        | where EventType == "Tornado"
        | project BeginLon, BeginLat
        | where isnotnull(BeginLat) and isnotnull(BeginLon)
        | summarize count_summary=count() by hash = geo_point_to_s2cell(BeginLon, BeginLat, 4)
        | project geo_s2cell_to_central_point(hash), count_summary
        | extend Events = "count"
        | render piechart with (kind = map)

#### Mostrar puntos dentro de un área específica

        let southern_california = dynamic({
            "type": "Polygon",
            "coordinates": [[[-119.5, 34.5], [-115.5, 34.5], [-115.5, 32.5], [-119.5, 32.5], [-119.5, 34.5]]
            ]});
        StormEvents
        | where geo_point_in_polygon(BeginLon, BeginLat, southern_california)
        | project BeginLon, BeginLat
        | summarize count_summary = count() by hash = geo_point_to_s2cell(BeginLon, BeginLat, 8)
        | project geo_s2cell_to_central_point(hash), count_summary
        | extend Events = "count"
        | render piechart with (kind = map)

#### Mostrar puntos cercanos en un LineString

        let roadToKeyWest = dynamic({
        "type":"linestring",
        "coordinates":[
                [
                    -81.79595947265625,
                    24.56461038017685
                ],
                [
                    -81.595458984375,
                    24.627044746156027
                ],
                [
                    -81.52130126953125,
                    24.666986385216273
                ],
                [
                    -81.35650634765625,
                    24.66449040712424
                ],
                [
                    -81.32354736328125,
                    24.647017162630366
                ],
                [
                    -80.8099365234375,
                    24.821639356846607
                ],
                [
                    -80.62042236328125,
                    24.93127614538456
                ],
                [
                    -80.37872314453125,
                    25.175116531621764
                ],
                [
                    -80.42266845703124,
                    25.19251511519153
                ],
                [
                    -80.4803466796875,
                    25.46063471847754
                ]
                ]});
        StormEvents
        | where isnotempty(BeginLat) and isnotempty(BeginLon)
        | project BeginLon, BeginLat, EventType
        | where geo_distance_point_to_line(BeginLon, BeginLat, roadToKeyWest) < 500
        | render scatterchart with (kind=map)

#### Mostrar puntos cercanos en un polígono

        let roadToKeyWest = dynamic({
        "type":"polygon",
        "coordinates":[
                [
                    [
                    -80.08209228515625,
                    25.39117928167583
                    ],
                    [
                    -80.4913330078125,
                    25.517657429994035
                    ],
                    [
                    -80.57922363281249,
                    25.477992320574817
                    ],
                    [
                    -82.188720703125,
                    24.632038149596895
                    ],
                    [
                    -82.1942138671875,
                    24.53712939907993
                    ],
                    [
                    -82.13104248046875,
                    24.412140070651528
                    ],
                    [
                    -81.81243896484375,
                    24.43714786161562
                    ],
                    [
                    -80.58746337890625,
                    24.794214972389486
                    ],
                    [
                    -80.08209228515625,
                    25.39117928167583
                    ]
                ]
                ]});
        StormEvents
        | where isnotempty(BeginLat) and isnotempty(BeginLon)
        | project BeginLon, BeginLat, EventType
        | where geo_distance_point_to_polygon(BeginLon, BeginLat, roadToKeyWest) < 500
        | render scatterchart with (kind=map)

#### Encuentre anomalías en función de datos geoespaciales

        let stateOfInterest = "Texas";
        let statePolygon = materialize(
            US_States
            | extend name = tostring(features.properties.NAME)
            | where name == stateOfInterest
            | project geometry=features.geometry);
        let stateCoveringS2cells = statePolygon
            | project s2Cells = geo_polygon_to_s2cells(geometry, 9);
        StormEvents
        | extend s2Cell = geo_point_to_s2cell(BeginLon, BeginLat, 9)
        | where s2Cell in (stateCoveringS2cells)
        | where geo_point_in_polygon(BeginLon, BeginLat, toscalar(statePolygon))
        | make-series damage = avg(DamageProperty + DamageCrops) default = double(0.0) on StartTime step 7d
        | extend anomalies=series_decompose_anomalies(damage)
        | render anomalychart with (anomalycolumns=anomalies)

> [!NOTE]
> Para ver las imagenes de los resultados de las consultas de ejemplos visitad esta [web](https://learn.microsoft.com/gl-es/kusto/query/tutorials/create-geospatial-visualizations?view=azure-data-explorer).

## Referencias

[Microsoft Learn](https://learn.microsoft.com/es-es/kusto/query/?view=microsoft-fabric)