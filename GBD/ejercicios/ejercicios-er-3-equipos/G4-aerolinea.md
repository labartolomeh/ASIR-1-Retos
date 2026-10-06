# GBD · Ejercicios E/R 3 · G4 · Aerolínea

Ejercicio de diseño de bases de datos: del enunciado al diagrama entidad/relación, y del diagrama
a las tablas en DrawDB. Se trabaja en clase en equipo y se presenta a los compañeros.

## Qué tenéis que hacer

| Paso | Qué | Tiempo en clase |
|---|---|---|
| 1 | Borrador del diagrama E/R en papel: entidades, atributos, relaciones y cardinalidades | 15 min |
| 2 | Esquema de tablas en **DrawDB**: tablas, columnas con su tipo, claves primarias y ajenas, qué admite nulo, claves alternativas | 25 min |
| 3 | Comprobación: cada pregunta del enunciado se tiene que poder contestar recorriendo vuestras tablas. Lista de las reglas del enunciado que ni el diagrama ni las tablas garantizan | 10 min |
| 4 | Presentación a la clase, con DrawDB proyectado | 5 min |

Teoría: `teoria-2-er-y-relacional.md`, sobre todo las reglas de paso a tablas 1 a 11. Ejemplos
resueltos: `ejercicios-er-2.md`.

## Qué se sube al repositorio

En la carpeta `bd/ejercicio-equipo/` de vuestro repositorio:

| Fichero | Qué |
|---|---|
| Este enunciado | Tal cual |
| `borrador-er.jpg` | Foto legible del borrador en papel |
| `esquema.json` | El esquema exportado de DrawDB, para poder abrirlo otra vez |
| `esquema.png` | El esquema como imagen |
| `esquema.sql` | El SQL que genera DrawDB |
| `respuestas.md` | Para cada pregunta, qué tablas se miran y por qué columnas se enlazan (una línea por pregunta). Debajo, la lista de restricciones que no caben, diciendo dónde se garantizaría cada una. Y las decisiones dudosas, con una línea de por qué |

## DrawDB en cinco pasos

[drawdb.app](https://drawdb.app) → *Try it* → base de datos **MariaDB**. No hace falta cuenta.

1. **Tabla:** *Add table*. Doble clic para cambiar el nombre.
2. **Columnas:** nombre y tipo. Marcad la clave primaria (icono de llave; varias columnas si es
   compuesta), *not null* y *unique* donde toque.
3. **Clave ajena:** arrastrad desde el punto de la columna (`id_jefe`) hasta la columna a la que
   apunta (`id_empleado`), aunque esté en la misma tabla. Elegid la cardinalidad y qué pasa al
   borrar (`RESTRICT`, `SET NULL`, `CASCADE`).
4. **Guardar:** DrawDB guarda solo en el navegador de ese ordenador. Desde el menú *File*, exportad
   a **JSON** a mitad del trabajo y al final, no solo al final.
5. **Imagen y SQL:** exportad a **PNG** para presentar y el código **SQL** para el repositorio.

DrawDB dibuja las relaciones en pata de gallo, no con rombos. Una clave ajena compuesta (la de una
entidad débil) aparece como varias líneas: es normal.

## Cómo se presenta

| Minuto | Qué |
|---|---|
| 0–3 | Una persona cuenta el enunciado en una frase. Otra recorre el esquema tabla a tabla: de qué entidad o relación del E/R sale cada una, y por qué regla |
| 3–5 | Otra persona contesta en voz alta una de las preguntas recorriendo las tablas |
| Después | La clase pregunta. El profesor elige quién del equipo contesta |

Quien escucha busca **una cardinalidad con la que no esté de acuerdo** o **una pregunta que el
esquema no conteste**. Se debate en la pizarra.

## Enunciado

> Una aerolínea regional guarda sus aeropuertos (código IATA de tres letras como `ZAZ`, nombre,
> ciudad y país) y sus aviones (matrícula, modelo y año). Los asientos de cada avión se identifican
> por fila y letra **dentro del avión** —el 12C existe en todos— y cada uno es de clase turista o
> business.
>
> Cada vuelo tiene un código comercial (`IB3456`), una fecha, hora de salida y de llegada, un
> aeropuerto de origen y uno de destino, y lo hace un avión. El mismo código se repite cada día.
>
> Los pasajeros (documento, nombre, fecha de nacimiento, email) reservan plaza en vuelos. Al
> reservar se elige asiento, y se guarda el precio pagado. En un vuelo, un asiento es de un solo
> pasajero, y un pasajero tiene un solo asiento.
>
> La tripulación son pilotos (número de licencia y horas de vuelo) y auxiliares de cabina (con los
> idiomas que hablan); todos tienen número de empleado y nombre. Cada piloto nuevo tiene asignado
> un piloto instructor. En cada vuelo trabajan varios tripulantes, cada uno con una función
> (comandante, copiloto, jefe de cabina, auxiliar).

## Preguntas que tiene que contestar

1. ¿Qué asientos quedan libres en el vuelo IB3456 del 30 de septiembre?
2. ¿Qué vuelos salen de Zaragoza y llegan a Palma?
3. ¿Quién fue el comandante de un vuelo, y quién es su instructor?
4. ¿Qué auxiliares hablan francés y en qué vuelos han trabajado este mes?
5. ¿Cuántas horas duró cada vuelo?
