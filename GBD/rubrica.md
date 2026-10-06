# Rúbrica · Reto 0 · GBD

Matriz de evidencias por criterio de evaluación, con el mismo formato que la rúbrica del reto de
Fundamentos de Hardware e ISO. Cada criterio se registra como:

- **A** → Apto
- **NA** → No apto
- **NE** → No evaluado todavía

Un CE que no se trabaja en este reto se marca **NE**, no como suspenso.

Entregables E1–E10: ver [`encargo.md`](encargo.md).

---

## RA1. Reconoce los elementos de las bases de datos analizando sus funciones y valorando la utilidad de sistemas gestores

| CE | Evidencia en el reto | Apto cuando… | Resultado |
|---|---|---|---|
| **RA1.a** Se han analizado los distintos sistemas lógicos de almacenamiento y sus funciones. | E1, E3, E10 | Distingue fichero de texto y binario, lee un CSV (cabecera, separador, comillas) y explica qué no puede garantizar una hoja de cálculo: tipos, dominios, integridad, concurrencia | ☐ A ☐ NA ☐ NE |
| **RA1.b** Se han identificado los distintos tipos de bases de datos según el modelo de datos utilizado. | E2, E10 | Sitúa el gestor investigado como relacional, documental o clave-valor y sabe qué cambia en cada caso | ☐ A ☐ NA ☐ NE |
| **RA1.c** Se han identificado los distintos tipos de bases de datos en función de la ubicación de la información. | E2, E10 | Distingue base de datos embebida, en servidor propio y en la nube, con un ejemplo de cada una | ☐ A ☐ NA ☐ NE |
| **RA1.d** Se ha reconocido la utilidad de un sistema gestor de bases de datos. | E3, E9 | Relaciona al menos cuatro problemas de su propia hoja con lo que aporta el SGBD: tipos, integridad referencial, concurrencia, permisos, copias, consultas | ☐ A ☐ NA ☐ NE |
| **RA1.e** Se ha descrito la función de cada uno de los elementos de un sistema gestor de bases de datos. | E10 | Nombra motor, diccionario de datos, lenguajes de definición y manipulación, gestor de transacciones y de copias, y dice qué hace cada uno | ☐ A ☐ NA ☐ NE |
| **RA1.f** Se han clasificado los sistemas gestores de bases de datos. | E2 | Clasifica los seis gestores investigados en clase por modelo, licencia y ámbito de uso, y justifica la elección de MariaDB para el reto | ☐ A ☐ NA ☐ NE |

---

## RA2. Diseña modelos lógicos normalizados interpretando diagramas entidad/relación

| CE | Evidencia en el reto | Apto cuando… | Resultado |
|---|---|---|---|
| **RA2.a** Se ha identificado el significado de la simbología propia de los diagramas entidad/relación. | E4, E9 | Usa correctamente entidad, atributo, relación, clave y cardinalidad `(mín,máx)`, y lee un diagrama ajeno en voz alta como frases | ☐ A ☐ NA ☐ NE |
| **RA2.b** Se han utilizado herramientas gráficas para representar el diseño lógico. | E4, E6 | E/R en draw.io y esquema de tablas en DrawDB, coherentes entre sí | ☐ A ☐ NA ☐ NE |
| **RA2.c** Se han identificado las tablas del diseño lógico. | E6 | Cada entidad y cada relación N:M tienen su tabla; las 1:N no generan tabla propia | ☐ A ☐ NA ☐ NE |
| **RA2.d** Se han identificado los campos que forman parte de las tablas del diseño lógico. | E6 | Cada campo está en una sola tabla y en la que le corresponde; los atributos de relación están en la tabla de la relación o en el lado N | ☐ A ☐ NA ☐ NE |
| **RA2.e** Se han identificado las relaciones entre las tablas del diseño lógico. | E4, E6 | Cardinalidades justificadas con las dos preguntas; el caso del componente suelto y el de «procede de» frente a «montado en» resueltos | ☐ A ☐ NA ☐ NE |
| **RA2.f** Se han definido los campos clave. | E4, E6, E9 | Clave primaria en cada tabla, subrogada donde no hay natural (etiqueta), y clave ajena en cada relación. Explica por qué el nombre o el número de serie no sirven como clave | ☐ A ☐ NA ☐ NE |
| **RA2.g** Se han aplicado las reglas de integridad. | E6, E7 | Claves ajenas declaradas; un intento de cargar `EQ-4` en lugar de `EQ-04` es rechazado por el gestor | ☐ A ☐ NA ☐ NE |
| **RA2.h** Se han aplicado las reglas de normalización hasta un nivel adecuado. | — | No se trabaja en este reto. Reto 1 | ☐ NE |
| **RA2.i** Se han identificado y documentado las restricciones que no pueden plasmarse en el diseño lógico. | E5 | Al menos tres restricciones reales de su inventario, con dónde se garantizaría cada una | ☐ A ☐ NA ☐ NE |

---

## RA3. Realiza el diseño físico de bases de datos utilizando asistentes, herramientas gráficas y el lenguaje de definición de datos

Solo los CE que se trabajan al implementar el modelo. El resto se completa en el Reto 1.

| CE | Evidencia en el reto | Apto cuando… | Resultado |
|---|---|---|---|
| **RA3.b** Se han creado tablas. | E7 | Las tablas existen en el MariaDB del equipo y coinciden con el esquema de E6 | ☐ A ☐ NA ☐ NE |
| **RA3.c** Se han seleccionado los tipos de datos adecuados. | E1, E6, E7 | Números como números con unidad fija en el nombre de la columna; códigos y números de serie como texto; booleanos y fechas con su tipo. Ninguna capacidad guardada como «4 GB» | ☐ A ☐ NA ☐ NE |
| **RA3.d** Se han definido los campos clave en las tablas. | E7 | Claves primarias y ajenas declaradas en la base de datos, no solo dibujadas | ☐ A ☐ NA ☐ NE |
| **RA3.f** Se ha verificado mediante un conjunto de datos de prueba que la implementación se ajusta al modelo. | E7 | Los datos reales del despiece se cargan sin tener que cambiar el modelo, o el cambio queda documentado | ☐ A ☐ NA ☐ NE |
| **RA3.g** Se han utilizado asistentes y herramientas gráficas. | E6, E7 | DrawDB para el esquema y DBeaver para crear e importar | ☐ A ☐ NA ☐ NE |
| **RA3.h** Se ha utilizado el lenguaje de definición de datos. | E6, E7 | Ejecuta el SQL generado por DrawDB y sabe leer qué hace cada `CREATE TABLE`. No se pide escribirlo desde cero | ☐ A ☐ NA ☐ NE |
| **RA3.a, e, i** | — | Reto 1 | ☐ NE |

---

## RA4. Consulta la información almacenada manejando asistentes, herramientas gráficas y el lenguaje de manipulación de datos

| CE | Evidencia en el reto | Apto cuando… | Resultado |
|---|---|---|---|
| **RA4.a** Se han identificado las herramientas y sentencias para realizar consultas. | E8 | Ejecuta consultas en DBeaver y distingue `SELECT`, `WHERE`, `ORDER BY` y las funciones de resumen | ☐ A ☐ NA ☐ NE |
| **RA4.b** Se han realizado consultas simples sobre una tabla. | E8 | Preguntas que se resuelven en una tabla con filtro y orden, con resultado correcto sobre sus datos | ☐ A ☐ NA ☐ NE |
| **RA4.c** Se han realizado consultas que generan valores de resumen. | E8 | Preguntas 1, 3, 5, 7 y 9: `COUNT`, `SUM`, `MAX` y `GROUP BY` con resultado correcto | ☐ A ☐ NA ☐ NE |
| **RA4.d** Se han realizado consultas sobre el contenido de varias tablas mediante composiciones internas. | E8 | Preguntas 2, 4, 6, 8 y 10, que cruzan dos tablas. Se inicia; se cierra en el Reto 1 | ☐ A ☐ NA ☐ NE |
| **RA4.e, f, g** | — | Reto 1 | ☐ NE |

---

## Selección de CE para este reto

| RA | CE trabajados | CE que quedan NE |
|---|---|---|
| RA1 | a, b, c, d, e, f | — |
| RA2 | a, b, c, d, e, f, g, i | h |
| RA3 | b, c, d, f, g, h | a, e, i |
| RA4 | a, b, c, d | e, f, g |

---

## Relación entre evidencias y CE

| Evidencia | RA1 | RA2 | RA3 | RA4 |
|---|---|---|---|---|
| E1 · Hoja con tipos y unidades | a | | c | |
| E2 · Ficha del gestor | b, c, f | | | |
| E3 · Catálogo de problemas | a, d | | | |
| E4 · Diagrama E/R | | a, b, e, f | | |
| E5 · Restricciones no representables | | i | | |
| E6 · Esquema de tablas y SQL | | b, c, d, e, f, g | c, g, h | |
| E7 · Base de datos con datos reales | | g | b, c, d, f, g, h | |
| E8 · Catálogo de consultas | | | | a, b, c, d |
| E9 · Defensa individual | d | a, f | | |
| E10 · Prueba escrita | a, b, c, e | | | |

---

## Registro individual

| Alumno/a | 1a | 1b | 1c | 1d | 1e | 1f | 2a | 2b | 2c | 2d | 2e | 2f | 2g | 2i | 3b | 3c | 3d | 3f | 3g | 3h | 4a | 4b | 4c | 4d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | | | | | | | | | | | | | | | | |
| | | | | | | | | | | | | | | | | | | | | | | | | |

---

## Criterios de uso

- Un CE no trabajado no está suspenso: se registra NE.
- Se evalúan evidencias, no tareas: E7 sirve a la vez para RA2.g y para seis CE de RA3.
- La evidencia tiene que ser individual. Los entregables de equipo se confirman con E9 y E10 y
  con la observación en clase durante las fases 3 y 4; sin esa confirmación, el CE queda NE
  para esa persona, no A.
- Un modelo que necesita corregirse al cargar los datos reales no es un NA: es un A en RA3.f si
  el cambio queda documentado y justificado.
- Consultar documentación, preguntar a otro equipo o usar el SQL generado por una herramienta no
  convierte un CE en NA.

## Apto y no apto

Apto: realiza lo que describe el CE, con autonomía, con resultado correcto sobre sus propios
datos, y lo explica.

No apto: no lo consigue, hay errores de fondo (clave repetida, capacidad como texto, clave ajena
sin declarar), necesita ayuda continua, o no puede justificar la decisión.
