# Prueba Técnica

## Paso 1: Alcance del proyecto y captura de datos
 
Los datos que se van a utilizar en este proyecto "Base.csv", encontrados en los datasets 
de kaggle, contiene datos simulados de transacciones de clientes de una institución bancaria
(Bank Account Fraud, BAF), donde cada instancia (fila) del archivo corresponde a una transacción
individual, estos fueron recolectados durante 8 meses.

Incluye datos sobre la transacción si fue fraudulenta, el porcentaje
de ingresos, la similitud en el nombre del correo, el número de meses en la residencia anterior,
el número de meses de en la residencia actual, la edad del cliente, los días desde la solicitud 
de la transacción, el monto de la transacción intencionado, el tipo de pago, el número de códigos
postales en 4 semanas, la velocidad en 6 y 24 horas, y en 4 semanas, el número de sucursales bancarias
en 8 semanas, el número de correos electrónicos distintos con la fecha de nacimiento en 4 semanas,
el estado laboral, el puntaje de riesgo crediticio, si el correo electrónico es gratis, el estado
de vivienda, si el teléfono de casa es válido, si el teléfono móvil es válido, el número de meses
en el banco, si tiene otras tarjetas, el límite de crédito propuesto, si la solicitud es extranjera,
el origen, la duración de la sesión en minutos, el sistema operativo del dispositivo, si la sesión
fue mantenida activa, el número de correos electrónicos distintos del dispositivo en 8 semanas,
el número de fraudes del dispositivo, y el mes.

Estos datos se van a utilizar con el objetivo de detectar fraudes, los datos de transacciones y cuentas 
se pueden utilizar para detectar transacciones fraudulentas. El sistema debe ser capaz de identificar y 
clasificar transacciones fraudulentas con una alta precisión; además, debe ser capaz de escalar para manejar
grandes volúmenes de datos. El sistema se basará en un modelo de aprendizaje automático que será entrenado 
en un conjunto de datos de transacciones fraudulentas y no fraudulentas; el modelo será capaz de identificar
patrones en los datos que son indicativos de fraude. Con el sistema de detección de fraude se pretende ayudar
a proteger al banco de pérdidas financieras y a mantener la seguridad de sus clientes.

## Paso 2: Explorar y evaluar los datos, el EDA

### Análisis de calida de datos.

**Auditoría de datos de 32 campos y 1'000.000 de variables**

Se construyé una auditoría de datos a partir de la herramienta de SPSS Modeler.
Se encuentra una base de datos con un millon de registros con 32 variables, de las cuales 27 son variables númericas y 5
categoricas, las variables traen todos los valores válidos para cada uno de los registros, lo que nos genera una 
completitud del 100% a nivel de filas y columnas, esto es común en archivos transaccionales dado que la información se 
exporta a partir de un software transaccional que construye toda la información y no genera perdida de información.

Para cada una de las variables se genera los descriptivos siempre y cuando sean variables numericas y esto es consistente
para el tipo de dato.

|    |                                      |                          |          |          |            |                |           |          |                         |                |             |           |                        |          |                       |           |         |
|----|--------------------------------------|--------------------------|----------|----------|------------|----------------|-----------|----------|-------------------------|----------------|-------------|-----------|------------------------|----------|-----------------------|-----------|---------|
|    | Campo                                | Gráfico de muestras      | Medida   | Mín.     | Máx.       | Suma           | Rango     | Media    | Error estándar de media | Desv. estándar | Varianza    | Asimetría | Err. típ. de asimetría | Kurtosis | Err. típ. de Kurtosis | Exclusivo | Válido  |
| 1  | fraud_bool                           | ![](/Graficos/prop1.jpg) | Continuo | 0        | 1          | 11029          | 1         | 0.011    | 0.000                   | 0.104          | 0.011       | 9.364     | 0.002                  | 85.682   | 0.005                 | --        | 1000000 |
| 2  | income                               | ![](Graficos/prop2.jpg)  | Continuo | 0.100    | 0.900      | 562695.600     | 0.800     | 0.563    | 0.000                   | 0.290          | 0.084       | -0.386    | 0.002                  | -1.299   | 0.005                 | --        | 1000000 |
| 3  | name\_email\_similarity              | ![](Graficos/prop3.jpg)  | Continuo | 0.000    | 1.000      | 493694.095     | 1.000     | 0.494    | 0.000                   | 0.289          | 0.084       | 0.043     | 0.002                  | -1.280   | 0.005                 | --        | 1000000 |
| 4  | prev\_address\_months_count          | ![](Graficos/prop4.jpg)  | Continuo | -1       | 383        | 16718568       | 384       | 16.719   | 0.044                   | 44.046         | 1940.070    | 4.064     | 0.002                  | 20.031   | 0.005                 | --        | 1000000 |
| 5  | current\_address\_months_count       | ![](Graficos/prop5.jpg)  | Continuo | -1       | 428        | 86587867       | 429       | 86.588   | 0.088                   | 88.407         | 7815.727    | 1.387     | 0.002                  | 1.357    | 0.005                 | --        | 1000000 |
| 6  | customer_age                         | ![](Graficos/prop6.jpg)  | Continuo | 10       | 90         | 33689080       | 80        | 33.689   | 0.012                   | 12.026         | 144.620     | 0.478     | 0.002                  | -0.115   | 0.005                 | --        | 1000000 |
| 7  | days\_since\_request                 | ![](Graficos/prop7.jpg)  | Continuo | 0.000    | 78.457     | 1025705.231    | 78.457    | 1.026    | 0.005                   | 5.382          | 28.964      | 9.279     | 0.002                  | 106.569  | 0.005                 | --        | 1000000 |
| 8  | intended\_balcon\_amount             | ![](Graficos/prop8.jpg)  | Continuo | -15.531  | 112.957    | 8661498.537    | 128.487   | 8.661    | 0.020                   | 20.236         | 409.502     | 2.507     | 0.002                  | 6.847    | 0.005                 | --        | 1000000 |
| 9  | payment_type                         | ![](Graficos/prop9.jpg)  | Nominal  | --       | --         | --             | --        | --       | --                      | --             | --          | --        | --                     | --       | --                    | 5         | 1000000 |
| 10 | zip\_count\_4w                       | ![](Graficos/prop10.jpg) | Continuo | 1        | 6700       | 1572692049     | 6699      | 1572.692 | 1.005                   | 1005.375       | 1010778.016 | 1.457     | 0.002                  | 2.140    | 0.005                 | --        | 1000000 |
| 11 | velocity_6h                          | ![](Graficos/prop11.jpg) | Continuo | -170.603 | 16715.565  | 5665296604.795 | 16886.168 | 5665.297 | 3.009                   | 3009.381       | 9056371.989 | 0.563     | 0.002                  | 0.003    | 0.005                 | --        | 1000000 |
| 12 | velocity_24h                         | ![](Graficos/prop12.jpg) | Continuo | 1300.307 | 9506.897   | 4769781964.962 | 8206.589  | 4769.782 | 1.479                   | 1479.213       | 2188069.952 | 0.331     | 0.002                  | -0.374   | 0.005                 | --        | 1000000 |
| 13 | velocity_4w                          | ![](Graficos/prop13.jpg) | Continuo | 2825.748 | 6994.764   | 4856324015.812 | 4169.016  | 4856.324 | 0.920                   | 919.844        | 846112.863  | -0.060    | 0.002                  | -0.360   | 0.005                 | --        | 1000000 |
| 14 | bank\_branch\_count_8w               | ![](Graficos/prop14.jpg) | Continuo | 0        | 2385       | 184361849      | 2385      | 184.362  | 0.460                   | 459.625        | 211255.443  | 2.747     | 0.002                  | 6.503    | 0.005                 | --        | 1000000 |
| 15 | date\_of\_birth\_distinct\_emails_4w | ![](Graficos/prop15.jpg) | Continuo | 0        | 39         | 9503544        | 39        | 9.504    | 0.005                   | 5.034          | 25.339      | 0.703     | 0.002                  | 0.436    | 0.005                 | --        | 1000000 |
| 16 | employment_status                    | ![](Graficos/prop16.jpg) | Nominal  | --       | --         | --             | --        | --       | --                      | --             | --          | --        | --                     | --       | --                    | 7         | 1000000 |
| 17 | credit\_risk\_score                  | ![](Graficos/prop17.jpg) | Continuo | -170     | 389        | 130989595      | 559       | 130.990  | 0.070                   | 69.682         | 4855.555    | 0.296     | 0.002                  | 0.068    | 0.005                 | --        | 1000000 |
| 18 | email\_is\_free                      | ![](Graficos/prop18.jpg) | Continuo | 0        | 1          | 529886         | 1         | 0.530    | 0.000                   | 0.499          | 0.249       | -0.120    | 0.002                  | -1.986   | 0.005                 | --        | 1000000 |
| 19 | housing_status                       | ![](Graficos/prop19.jpg) | Nominal  | --       | --         | --             | --        | --       | --                      | --             | --          | --        | --                     | --       | --                    | 7         | 1000000 |
| 20 | phone\_home\_valid                   | ![](Graficos/prop20.jpg) | Continuo | 0        | 1          | 417077         | 1         | 0.417    | 0.000                   | 0.493          | 0.243       | 0.336     | 0.002                  | -1.887   | 0.005                 | --        | 1000000 |
| 21 | phone\_mobile\_valid                 | ![](Graficos/prop21.jpg) | Continuo | 0        | 1          | 889676         | 1         | 0.890    | 0.000                   | 0.313          | 0.098       | -2.488    | 0.002                  | 4.188    | 0.005                 | --        | 1000000 |
| 22 | bank\_months\_count                  | ![](Graficos/prop22.jpg) | Continuo | -1       | 32         | 10839303       | 33        | 10.839   | 0.012                   | 12.117         | 146.819     | 0.489     | 0.002                  | -1.436   | 0.005                 | --        | 1000000 |
| 23 | has\_other\_cards                    | ![](Graficos/prop23.jpg) | Continuo | 0        | 1          | 222988         | 1         | 0.223    | 0.000                   | 0.416          | 0.173       | 1.331     | 0.002                  | -0.228   | 0.005                 | --        | 1000000 |
| 24 | proposed\_credit\_limit              | ![](Graficos/prop24.jpg) | Continuo | 190.000  | 2100.000   | 515851010.000  | 1910.000  | 515.851  | 0.488                   | 487.560        | 237714.658  | 1.301     | 0.002                  | 0.169    | 0.005                 | --        | 1000000 |
| 25 | foreign_request                      | ![](Graficos/prop25.jpg) | Continuo | 0        | 1          | 25242          | 1         | 0.025    | 0.000                   | 0.157          | 0.025       | 6.053     | 0.002                  | 34.643   | 0.005                 | --        | 1000000 |
| 26 | source                               | ![](Graficos/prop26.jpg) | Marca    | --       | --         | --             | --        | --       | --                      | --             | --          | --        | --                     | --       | --                    | 2         | 1000000 |
| 27 | session\_length\_in_minutes          | ![](Graficos/prop27.jpg) | Continuo | -1.000   | 85.899     | 7544940.201    | 86.899    | 7.545    | 0.008                   | 8.033          | 64.531      | 3.305     | 0.002                  | 14.961   | 0.005                 | --        | 1000000 |
| 28 | device_os                            | ![](Graficos/prop28.jpg) | Nominal  | --       | --         | --             | --        | --       | --                      | --             | --          | --        | --                     | --       | --                    | 5         | 1000000 |
| 29 | keep\_alive\_session                 | ![](Graficos/prop29.jpg) | Continuo | 0        | 1          | 576947         | 1         | 0.577    | 0.000                   | 0.494          | 0.244       | -0.311    | 0.002                  | -1.903   | 0.005                 | --        | 1000000 |
| 30 | device\_distinct\_emails_8w          | ![](Graficos/prop30.jpg) | Continuo | -1       | 2          | 1018312        | 3         | 1.018    | 0.000                   | 0.181          | 0.033       | 2.431     | 0.002                  | 30.907   | 0.005                 | --        | 1000000 |
| 31 | device\_fraud\_count                 | ![](Graficos/prop31.jpg) | Continuo | 0        | 0          |  0             | 0         | 0        | 0                       | 0              | 0           | --        | --                     | --       | --                    | --        | 1000000 |
| 32 | month                                | ![](Graficos/prop32.jpg) | Continuo | 0        | 7          | 3288674        | 7         | 3.289    | 0.002                   | 2.210          | 4.884       | 0.112     | 0.002                  | -1.128   | 0.005                 | --        | 1000000 |



En el analisis de calidad se encuentran valores atípicos, a más de 3 desviaciones estandar a partir de la media y valores
extremos, a más de 5 desviaciones estandar a parir de la media, en 16 de los 32 campos.

 

|    |                                      |          |                  |          |             |                   |            |              |                   |                 |
|----|--------------------------------------|----------|------------------|----------|-------------|-------------------|------------|--------------|-------------------|-----------------|
|    | Campo                                | Medida   | Valores atípicos | Extremos |  % Completo | Registros válidos | Valor nulo | Cadena vacía | Espacio en blanco | Valor en blanco |
| 1  | fraud_bool                           | Continuo | 0                | 11029    |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 2  | income                               | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 3  | name\_email\_similarity              | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 4  | prev\_address\_months_count          | Continuo | 15857            | 9453     |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 5  | current\_address\_months_count       | Continuo | 21483            | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 6  | customer_age                         | Continuo | 7890             | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 7  | days\_since\_request                 | Continuo | 12501            | 5274     |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 8  | intended\_balcon\_amount             | Continuo | 18749            | 211      |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 9  | payment_type                         | Nominal  | --               | --       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 10 | zip\_count\_4w                       | Continuo | 16244            | 3        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 11 | velocity_6h                          | Continuo | 4341             | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 12 | velocity_24h                         | Continuo | 539              | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 13 | velocity_4w                          | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 14 | bank\_branch\_count_8w               | Continuo | 40984            | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 15 | date\_of\_birth\_distinct\_emails_4w | Continuo | 6161             | 97       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 16 | employment_status                    | Nominal  | --               | --       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 17 | credit\_risk\_score                  | Continuo | 3471             | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 18 | email\_is\_free                      | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 19 | housing_status                       | Nominal  | --               | --       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 20 | phone\_home\_valid                   | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 21 | phone\_mobile\_valid                 | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 22 | bank\_months\_count                  | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 23 | has\_other\_cards                    | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 24 | proposed\_credit\_limit              | Continuo | 6155             | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 25 | foreign_request                      | Continuo | 0                | 25242    |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 26 | source                               | Marca    | --               | --       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 27 | session\_length\_in_minutes          | Continuo | 15530            | 8063     |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 28 | device_os                            | Nominal  | --               | --       |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 29 | keep\_alive\_session                 | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 30 | device\_distinct\_emails_8w          | Continuo | 0                | 31933    |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 31 | device\_fraud\_count                 | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 32 | month                                | Continuo | 0                | 0        |  100,000    | 1000000           | 0          | 0            | 0                 | 0               |

###



Para la limpieza de datos el primer paso es identificar los errores en el conjunto de datos. Esto se puede hacer mediante
visualizaciones de los datos, utilizando herramientas de análisis de datos o utilizando un conjunto de reglas para 
identificar errores específicos. Una vez que se han identificado los errores, deben corregirse. Esto implicaría la edición,
la eliminación de los datos o la creación de nuevos datos.

![](Graficos/Limpiar_los_datos.png)

Para esta base de datos no fue necesario hacer reemplazo o imputación de valores faltantes, dado que no existian, Los valores
faltantes pueden ser reemplazados por la media, la mediana o la moda del conjunto de datos; luego se debe hacer una reducción 
de valores atípicos, los valores atípicos son valores que se desvían significativamente del resto de los datos y pueden 
eliminarse o reemplazarse por valores cercanos; también se debe hacer una estandarización de datos para que todos los 
valores estén en la misma escala y esto pueda facilitar el análisis de los datos; los datos pueden ser transformados 
para que sean más fáciles de analizar, los datos categóricos pueden ser convertidos en datos numéricos, .

Como paso final, después de corregir los errores, los datos deben validarse para asegurarse de que están limpios. Esto 
se puede hacer con las técnicas utilizadas en el primer paso.



