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

@article{jesusTurningTablesBiased2022,
title={Turning the {{Tables}}: {{Biased}}, {{Imbalanced}}, {{Dynamic Tabular Datasets}} for {{ML Evaluation}}},
author={Jesus, S{\'e}rgio and Pombal, Jos{\'e} and Alves, Duarte and Cruz, Andr{\'e} and Saleiro, Pedro and Ribeiro, Rita P. and Gama, Jo{\~a}o and Bizarro, Pedro},
journal={Advances in Neural Information Processing Systems},
year={2022}
}

## Paso 2: Explorar y evaluar los datos, el EDA

### Análisis de calida de datos.

**Auditoría de datos de \[32 campos\]**

|    |                                      |                                                                                                          |          |          |           |                |           |          |                         |                |             |        |                        |          |                       |           |         |
|----|--------------------------------------|----------------------------------------------------------------------------------------------------------|----------|----------|-----------|----------------|-----------|----------|-------------------------|----------------|-------------|--------|------------------------|----------|-----------------------|-----------|---------|
|    | Campo                                | Gráfico de muestras                                                                                      | Medida   | Mín.     | Máx.      | Suma           | Rango     | Media    | Error estándar de media | Desv. estándar | Varianza    | Sesgo  | Err. típ. de asimetría | Kurtosis | Err. típ. de Kurtosis | Exclusivo | Válido  |
| 1  | fraud_bool                           | !\["fallo"](/Auditoría de datos de \[32 campos\]\_files//Auditoría de datos de \[32 campos\]\_prop1.jpg) | Continuo | 0        | 1         | 11029          | 1         | 0.011    | 0.000                   | 0.104          | 0.011       | 9.364  | 0.002                  | 85.682   | 0.005                 | --        | 1000000 |
| 2  | income                               | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop2.jpg)        | Continuo | 0.100    | 0.900     | 562695.600     | 0.800     | 0.563    | 0.000                   | 0.290          | 0.084       | -0.386 | 0.002                  | -1.299   | 0.005                 | --        | 1000000 |
| 3  | name\_email\_similarity              | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop3.jpg)        | Continuo | 0.000    | 1.000     | 493694.095     | 1.000     | 0.494    | 0.000                   | 0.289          | 0.084       | 0.043  | 0.002                  | -1.280   | 0.005                 | --        | 1000000 |
| 4  | prev\_address\_months_count          | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop4.jpg)        | Continuo | -1       | 383       | 16718568       | 384       | 16.719   | 0.044                   | 44.046         | 1940.070    | 4.064  | 0.002                  | 20.031   | 0.005                 | --        | 1000000 |
| 5  | current\_address\_months_count       | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop5.jpg)        | Continuo | -1       | 428       | 86587867       | 429       | 86.588   | 0.088                   | 88.407         | 7815.727    | 1.387  | 0.002                  | 1.357    | 0.005                 | --        | 1000000 |
| 6  | customer_age                         | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop6.jpg)        | Continuo | 10       | 90        | 33689080       | 80        | 33.689   | 0.012                   | 12.026         | 144.620     | 0.478  | 0.002                  | -0.115   | 0.005                 | --        | 1000000 |
| 7  | days\_since\_request                 | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop7.jpg)        | Continuo | 0.000    | 78.457    | 1025705.231    | 78.457    | 1.026    | 0.005                   | 5.382          | 28.964      | 9.279  | 0.002                  | 106.569  | 0.005                 | --        | 1000000 |
| 8  | intended\_balcon\_amount             | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop8.jpg)        | Continuo | -15.531  | 112.957   | 8661498.537    | 128.487   | 8.661    | 0.020                   | 20.236         | 409.502     | 2.507  | 0.002                  | 6.847    | 0.005                 | --        | 1000000 |
| 9  | payment_type                         | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop9.jpg)        | Nominal  | --       | --        | --             | --        | --       | --                      | --             | --          | --     | --                     | --       | --                    | 5         | 1000000 |
| 10 | zip\_count\_4w                       | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop10.jpg)       | Continuo | 1        | 6700      | 1572692049     | 6699      | 1572.692 | 1.005                   | 1005.375       | 1010778.016 | 1.457  | 0.002                  | 2.140    | 0.005                 | --        | 1000000 |
| 11 | velocity_6h                          | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop11.jpg)       | Continuo | -170.603 | 16715.565 | 5665296604.795 | 16886.168 | 5665.297 | 3.009                   | 3009.381       | 9056371.989 | 0.563  | 0.002                  | 0.003    | 0.005                 | --        | 1000000 |
| 12 | velocity_24h                         | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop12.jpg)       | Continuo | 1300.307 | 9506.897  | 4769781964.962 | 8206.589  | 4769.782 | 1.479                   | 1479.213       | 2188069.952 | 0.331  | 0.002                  | -0.374   | 0.005                 | --        | 1000000 |
| 13 | velocity_4w                          | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop13.jpg)       | Continuo | 2825.748 | 6994.764  | 4856324015.812 | 4169.016  | 4856.324 | 0.920                   | 919.844        | 846112.863  | -0.060 | 0.002                  | -0.360   | 0.005                 | --        | 1000000 |
| 14 | bank\_branch\_count_8w               | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop14.jpg)       | Continuo | 0        | 2385      | 184361849      | 2385      | 184.362  | 0.460                   | 459.625        | 211255.443  | 2.747  | 0.002                  | 6.503    | 0.005                 | --        | 1000000 |
| 15 | date\_of\_birth\_distinct\_emails_4w | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop15.jpg)       | Continuo | 0        | 39        | 9503544        | 39        | 9.504    | 0.005                   | 5.034          | 25.339      | 0.703  | 0.002                  | 0.436    | 0.005                 | --        | 1000000 |
| 16 | employment_status                    | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop16.jpg)       | Nominal  | --       | --        | --             | --        | --       | --                      | --             | --          | --     | --                     | --       | --                    | 7         | 1000000 |
| 17 | credit\_risk\_score                  | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop17.jpg)       | Continuo | -170     | 389       | 130989595      | 559       | 130.990  | 0.070                   | 69.682         | 4855.555    | 0.296  | 0.002                  | 0.068    | 0.005                 | --        | 1000000 |
| 18 | email\_is\_free                      | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop18.jpg)       | Continuo | 0        | 1         | 529886         | 1         | 0.530    | 0.000                   | 0.499          | 0.249       | -0.120 | 0.002                  | -1.986   | 0.005                 | --        | 1000000 |
| 19 | housing_status                       | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop19.jpg)       | Nominal  | --       | --        | --             | --        | --       | --                      | --             | --          | --     | --                     | --       | --                    | 7         | 1000000 |
| 20 | phone\_home\_valid                   | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop20.jpg)       | Continuo | 0        | 1         | 417077         | 1         | 0.417    | 0.000                   | 0.493          | 0.243       | 0.336  | 0.002                  | -1.887   | 0.005                 | --        | 1000000 |
| 21 | phone\_mobile\_valid                 | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop21.jpg)       | Continuo | 0        | 1         | 889676         | 1         | 0.890    | 0.000                   | 0.313          | 0.098       | -2.488 | 0.002                  | 4.188    | 0.005                 | --        | 1000000 |
| 22 | bank\_months\_count                  | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop22.jpg)       | Continuo | -1       | 32        | 10839303       | 33        | 10.839   | 0.012                   | 12.117         | 146.819     | 0.489  | 0.002                  | -1.436   | 0.005                 | --        | 1000000 |
| 23 | has\_other\_cards                    | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop23.jpg)       | Continuo | 0        | 1         | 222988         | 1         | 0.223    | 0.000                   | 0.416          | 0.173       | 1.331  | 0.002                  | -0.228   | 0.005                 | --        | 1000000 |
| 24 | proposed\_credit\_limit              | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop24.jpg)       | Continuo | 190.000  | 2100.000  | 515851010.000  | 1910.000  | 515.851  | 0.488                   | 487.560        | 237714.658  | 1.301  | 0.002                  | 0.169    | 0.005                 | --        | 1000000 |
| 25 | foreign_request                      | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop25.jpg)       | Continuo | 0        | 1         | 25242          | 1         | 0.025    | 0.000                   | 0.157          | 0.025       | 6.053  | 0.002                  | 34.643   | 0.005                 | --        | 1000000 |
| 26 | source                               | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop26.jpg)       | Marca    | --       | --        | --             | --        | --       | --                      | --             | --          | --     | --                     | --       | --                    | 2         | 1000000 |
| 27 | session\_length\_in_minutes          | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop27.jpg)       | Continuo | -1.000   | 85.899    | 7544940.201    | 86.899    | 7.545    | 0.008                   | 8.033          | 64.531      | 3.305  | 0.002                  | 14.961   | 0.005                 | --        | 1000000 |
| 28 | device_os                            | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop28.jpg)       | Nominal  | --       | --        | --             | --        | --       | --                      | --             | --          | --     | --                     | --       | --                    | 5         | 1000000 |
| 29 | keep\_alive\_session                 | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop29.jpg)       | Continuo | 0        | 1         | 576947         | 1         | 0.577    | 0.000                   | 0.494          | 0.244       | -0.311 | 0.002                  | -1.903   | 0.005                 | --        | 1000000 |
| 30 | device\_distinct\_emails_8w          | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop30.jpg)       | Continuo | -1       | 2         | 1018312        | 3         | 1.018    | 0.000                   | 0.181          | 0.033       | 2.431  | 0.002                  | 30.907   | 0.005                 | --        | 1000000 |
| 31 | device\_fraud\_count                 | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop31.jpg)       | Continuo | 0        | 0         | 0              | 0         | 0        | 0                       | 0              | 0           | --     | --                     | --       | --                    | --        | 1000000 |
| 32 | month                                | !\[\](Auditoría de datos de \[32 campos\]\_files\\Auditoría de datos de \[32 campos\]\_prop32.jpg)       | Continuo | 0        | 7         | 3288674        | 7         | 3.289    | 0.002                   | 2.210          | 4.884       | 0.112  | 0.002                  | -1.128   | 0.005                 | --        | 1000000 |



|    |                                      |          |                  |          |         |                  |        |            |                   |            |              |                   |                 |
|----|--------------------------------------|----------|------------------|----------|---------|------------------|--------|------------|-------------------|------------|--------------|-------------------|-----------------|
|    | Campo                                | Medida   | Valores atípicos | Extremos | Acción  | Imputar perdidos | Método | % Completo | Registros válidos | Valor nulo | Cadena vacía | Espacio en blanco | Valor en blanco |
| 1  | fraud_bool                           | Continuo | 0                | 11029    | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 2  | income                               | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 3  | name\_email\_similarity              | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 4  | prev\_address\_months_count          | Continuo | 15857            | 9453     | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 5  | current\_address\_months_count       | Continuo | 21483            | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 6  | customer_age                         | Continuo | 7890             | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 7  | days\_since\_request                 | Continuo | 12501            | 5274     | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 8  | intended\_balcon\_amount             | Continuo | 18749            | 211      | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 9  | payment_type                         | Nominal  | --               | --       | --      | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 10 | zip\_count\_4w                       | Continuo | 16244            | 3        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 11 | velocity_6h                          | Continuo | 4341             | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 12 | velocity_24h                         | Continuo | 539              | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 13 | velocity_4w                          | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 14 | bank\_branch\_count_8w               | Continuo | 40984            | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 15 | date\_of\_birth\_distinct\_emails_4w | Continuo | 6161             | 97       | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 16 | employment_status                    | Nominal  | --               | --       | --      | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 17 | credit\_risk\_score                  | Continuo | 3471             | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 18 | email\_is\_free                      | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 19 | housing_status                       | Nominal  | --               | --       | --      | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 20 | phone\_home\_valid                   | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 21 | phone\_mobile\_valid                 | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 22 | bank\_months\_count                  | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 23 | has\_other\_cards                    | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 24 | proposed\_credit\_limit              | Continuo | 6155             | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 25 | foreign_request                      | Continuo | 0                | 25242    | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 26 | source                               | Marca    | --               | --       | --      | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 27 | session\_length\_in_minutes          | Continuo | 15530            | 8063     | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 28 | device_os                            | Nominal  | --               | --       | --      | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 29 | keep\_alive\_session                 | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 30 | device\_distinct\_emails_8w          | Continuo | 0                | 31933    | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 31 | device\_fraud\_count                 | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |
| 32 | month                                | Continuo | 0                | 0        | Ninguno | Nunca            | Fijo   | 100,000    | 1000000           | 0          | 0            | 0                 | 0               |

### 
