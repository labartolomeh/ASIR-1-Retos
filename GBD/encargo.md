# Reto 0 · GBD — Encargo

Parte de bases de datos del **Reto 0 · Recuperación y digitalización del parque informático**,
compartido con Fundamentos de Hardware, Implantación de Sistemas Operativos y Digitalización.
Mismos equipos, mismo material, mismo tablero Kanban.

---

## Contexto

En Fundamentos de Hardware estáis despiezando, identificando y etiquetando el material del aula.
Todo eso lo estáis apuntando en una hoja de cálculo. Al final del reto, esa información tiene que
estar en una base de datos que conteste preguntas sobre el material sin abrir ninguna hoja.

La especificación son las preguntas, no las columnas.

## Lo que tiene que contestar la base de datos

| # | Pregunta |
|---|---|
| 1 | ¿Cuánta RAM hay en total en el aula? ¿Y en cada grupo? |
| 2 | ¿Cuál es la CPU más rápida que tenemos y en qué equipo está? |
| 3 | ¿Cuántos equipos arrancan, cuántos no y cuántos están sin probar? |
| 4 | ¿Qué componentes sueltos hay en el almacén y de qué equipo salió cada uno? |
| 5 | ¿Cuántos módulos de RAM DDR3 hay y cuántos GB suman? |
| 6 | ¿Qué CPU sueltas se pueden montar en la placa de un equipo dado? |
| 7 | ¿Qué fabricante acumula más componentes averiados? |
| 8 | ¿Qué componentes no se han revisado nunca y cuáles fallaron en su última revisión? |
| 9 | ¿Cuánta RAM tiene montada cada equipo? |
| 10 | ¿Qué componentes se han retirado al punto limpio y cuándo? |

Cada equipo añade al menos dos preguntas propias, salidas de su propio despiece.

## Fases

| Fase | Qué hacéis | Producto |
|---|---|---|
| 0 · Datos | Seguís registrando el despiece en vuestra hoja. Decidís tipo y unidad de cada columna | Hoja de FH con una fila de cabecera que indica tipo y unidad |
| 1 · Gestores | Investigáis un gestor de bases de datos asignado y lo comparáis con los de los demás equipos | Ficha comparativa |
| 2 · Problemas | Analizáis vuestra hoja: qué preguntas no contesta y qué está mal en ella | Catálogo de problemas de la hoja |
| 3 · Modelo | Diseñáis el modelo entidad/relación de vuestro inventario. Primero en papel, luego en draw.io | Diagrama E/R con claves y cardinalidades. Lista de restricciones que el diagrama no puede expresar |
| 4 · Tablas | Pasáis el E/R a tablas en DrawDB: tipos de datos, claves primarias y ajenas. Leéis el SQL que genera | Esquema de tablas y su SQL |
| 5 · Datos reales | Instaláis MariaDB en un equipo vuestro, creáis la base de datos y cargáis los datos de vuestro despiece | Base de datos con datos reales |
| 6 · Consultas | Escribís las consultas que contestan las preguntas | Catálogo de consultas con su resultado |
| 7 · Defensa | Cada persona defiende el modelo de su equipo | — |

Las fases 3 y 4 empiezan en clase, con tiempo de trabajo, y se terminan en el reto.
No hay una fase de normalización en este reto: vuelve en el Reto 1 sobre esta misma base de datos.

## Entregables

| # | Entregable | Equipo / individual | Formato |
|---|---|---|---|
| E1 | Hoja de FH con tipo y unidad por columna | Equipo | La hoja, con una fila añadida |
| E2 | Ficha comparativa del gestor asignado, con una prueba | Equipo | `bd/E2-ficha-gestor.md` y captura, con la plantilla de `investigacion-1-gestores.md` |
| E3 | Catálogo de problemas de la hoja | Equipo | Tabla: problema, dónde se ve, qué pasaría si no se arregla |
| E4 | Diagrama E/R | Equipo | draw.io, exportado a PDF. La foto del A3 de la primera sesión, como anexo |
| E5 | Restricciones no representables | Equipo | Lista, mínimo tres, con dónde se garantizaría cada una |
| E6 | Esquema de tablas | Equipo | DrawDB, exportado a imagen, y el SQL generado |
| E7 | Base de datos con datos reales | Equipo | En vuestro MariaDB, una base de datos por equipo. Mínimo: todo el material que haya despiezado el equipo |
| E8 | Catálogo de consultas | Equipo | Pregunta, consulta SQL y captura del resultado. Las diez de arriba más las propias |
| E9 | Defensa del modelo | Individual | Cinco preguntas del profesorado sobre el modelo del equipo, sin notas |
| E10 | Prueba escrita corta | Individual | Ficheros, tipos de datos, gestores. 25 minutos |

Todo lo del equipo va en la carpeta `bd/` de vuestro repositorio del reto, con el mismo tablero
Kanban que el resto del reto. El rol «Base de datos y documentación» del Kanban rota como los demás.

## Herramientas

| Para | Herramienta | Instalación |
|---|---|---|
| E/R | draw.io, biblioteca *Entity Relation* | Ninguna, en el navegador |
| Tablas y SQL de creación | DrawDB | Ninguna, en el navegador |
| Gestor de bases de datos | MariaDB | En un equipo vuestro. Lo instaláis y lo gestionáis vosotros |
| Crear la base de datos, cargar datos, consultar | DBeaver contra vuestro MariaDB | DBeaver está en los equipos del aula |

Notación del E/R: la de clase. Rectángulo para entidad, rombo para relación, elipse para atributo,
clave subrayada, cardinalidades `(mín,máx)` junto a cada entidad. DrawDB dibuja con otra notación
(pata de gallo); en la fase 4 se explica cómo se lee.


## Evaluación

Por criterios de evaluación, con la rúbrica del reto: cada criterio queda como apto, no apto o
no evaluado. El detalle está en [`rubrica.md`](rubrica.md).

| Evidencia | Peso orientativo |
|---|---|
| Entregables de equipo E1–E8 | 50 % |
| Defensa individual E9 | 30 % |
| Prueba escrita E10 | 20 % |

El trabajo se reparte; el conocimiento no. En la defensa se pregunta a cualquiera del equipo por
cualquier parte del modelo.

## Datos personales

En la base de datos no hay nombres reales de personas. Si el modelo necesita personas (quién
revisó un componente, quién despiezó un equipo), se usan alias: `G1-A`, `G1-B`. Los datos de
número de serie y etiqueta del material sí son reales.

## Ampliaciones

| Ampliación | Qué añade |
|---|---|
| Reservas | Los equipos prestables y quién los tiene cada franja. Añade una entidad con fechas y la restricción de no solapamiento |
| Catálogo de compatibilidad | Socket, tipo de memoria e interfaces como entidades propias, para que la pregunta 6 se conteste sin guardar «compatible sí/no» |
| Historial de revisiones | Cada prueba de cada componente, con fecha, herramienta y resultado. Convierte «funciona» en un historial |

---

Última actualización: 2 de octubre de 2026.
