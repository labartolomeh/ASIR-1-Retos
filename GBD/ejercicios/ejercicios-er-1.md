# GBD · Ejercicios E/R 1 · Del diagrama a las tablas

Cuatro ejercicios de dificultad creciente. En cada uno haces el **diagrama entidad/relación** en
papel, como en clase, y su **paso a tablas**. La teoría está en
[`teoria-2-er-y-relacional.md`](../teoria/teoria-2-er-y-relacional.md), apartados 1 y 2.

Es lo mismo que haréis con el inventario en el reto: primero el E/R, luego las tablas en DrawDB.

| # | Dominio | Qué practica |
|---|---|---|
| 1 | Estudios y videojuegos | Entidad, clave, 1:N, participación opcional. Clave ajena |
| 2 | Gimnasio | N:M. Tabla intermedia. Clave ajena que admite nulo |
| 3 | Tienda online | N:M con atributos. Dato derivado. Dato que cambia con el tiempo |
| 4 | Torneo de fútbol sala | Dos relaciones entre las mismas entidades. Entidad débil. Restricciones que no caben en el diseño |

---

## Qué se entrega de cada ejercicio

Para cada ejercicio entrega:

| # | Qué | Cómo |
|---|---|---|
| A | Diagrama E/R con atributos, claves y cardinalidades | En papel, foto legible |
| B | Tablas, con la notación del apartado 2 de la teoría | En texto |
| C | Para cada pregunta del enunciado, qué tablas hay que mirar y por qué columnas se enlazan | Una línea por pregunta |
| D | Restricciones que ni el diagrama ni las tablas recogen, y dónde se garantizaría cada una | Lista. Obligatorio en el 3 y el 4 |

La comprobación C es la importante: si una pregunta no se puede contestar recorriendo tus tablas,
el diseño está mal, aunque las reglas se hayan aplicado bien.

---

## Ejercicio 1 · Estudios y videojuegos

Una web de reseñas quiere guardar información sobre videojuegos y sobre los estudios que los
desarrollan. De cada estudio interesa su nombre, el país y el año en que se fundó. De cada juego,
el título, el año de lanzamiento, el género y la nota media de los usuarios. Cada juego lo
desarrolla un único estudio; un estudio puede haber desarrollado muchos juegos, y también puede
acabar de fundarse y no haber publicado ninguno todavía. Hay títulos que se repiten: existe un
*Doom* de 1993 y otro de 2016.

**Preguntas que tiene que contestar:**

1. ¿Qué juegos ha desarrollado un estudio dado?
2. ¿Qué estudios no han publicado ningún juego?
3. ¿Cuál es el juego mejor valorado de cada género?

**Antes de entregar, comprueba:**

- ¿Qué pasa con tu clave de JUEGO si das de alta los dos *Doom*?
- En tu diagrama, ¿se puede dar de alta un estudio sin juegos? ¿Y en tus tablas?
- ¿En qué tabla está la clave ajena? ¿Puede ser nula?

---

## Ejercicio 2 · Gimnasio

Un gimnasio ofrece actividades dirigidas: spinning, yoga, zumba. De cada actividad interesa el
nombre, el día de la semana, la hora y la sala donde se da. Cada actividad la imparte un monitor,
y cada monitor puede impartir varias. De los monitores se guarda nombre, teléfono y titulación.
Los socios, de los que se guarda nombre, email y fecha de alta, se apuntan a las actividades que
quieren: uno puede estar en varias y en una actividad hay muchos socios. Un socio puede darse de
alta y no apuntarse a nada. Una actividad puede existir en el horario sin que nadie se haya
apuntado todavía, y puede quedarse temporalmente sin monitor si este causa baja.

**Preguntas que tiene que contestar:**

1. ¿A qué actividades está apuntado un socio?
2. ¿Cuántos socios hay en cada actividad?
3. ¿Qué actividades no tienen monitor ahora mismo?

**Antes de entregar, comprueba:**

- Hay spinning el lunes a las 18:00 y el jueves a las 19:00. ¿Son dos filas de la misma tabla o dos
  tablas? ¿Qué las distingue?
- La sala, ¿atributo o entidad? ¿Qué frase del enunciado lo decide?
- ¿Cómo se refleja en las tablas que una actividad se quede sin monitor?
- ¿Dónde guardas quién está apuntado a qué? ¿Puede un socio apuntarse dos veces a la misma actividad?

---

## Ejercicio 3 · Tienda online

Una tienda online de componentes vende productos a clientes. De cada producto se guarda nombre,
categoría (memoria, disco, placa…), precio actual y unidades en almacén. De cada cliente, nombre,
email y dirección de envío. Un cliente hace pedidos; cada pedido es de un solo cliente y tiene
fecha y estado (pendiente, enviado, entregado). Un pedido lleva uno o varios productos, y de cada
producto dentro de un pedido hay que saber cuántas unidades se pidieron y a qué precio se
vendieron, porque el precio del producto cambia y la factura tiene que decir lo que se pagó
entonces, no lo que vale hoy. El total del pedido se muestra en pantalla pero no se guarda: se
calcula. Un producto puede estar en el catálogo sin que nadie lo haya comprado nunca.

**Preguntas que tiene que contestar:**

1. ¿Qué productos llevaba un pedido y cuánto costó en total?
2. ¿Cuánto ha gastado cada cliente este año?
3. ¿Qué productos no se han vendido nunca?
4. ¿A qué precio se vendió un producto en cada pedido, comparado con su precio actual?

**Antes de entregar, comprueba:**

- La tienda sube el precio de un producto mañana. ¿Cambia lo que dicen las facturas antiguas?
- ¿Dónde está la cantidad? ¿Por qué no puede estar ni en PEDIDO ni en PRODUCTO?
- ¿Tienes una columna `total` en algún sitio? ¿Debería estar?
- Un cliente compra el mismo producto en dos pedidos distintos. ¿Se distinguen las dos compras?
- «Un pedido lleva uno o varios productos»: ¿lo garantizan tus tablas?

---

## Ejercicio 4 · Torneo de fútbol sala

El instituto organiza un torneo de fútbol sala entre clases. Cada equipo tiene un nombre y
pertenece a un grupo-clase. Cada jugador juega en un solo equipo; de él se guarda nombre y dorsal,
y no puede haber dos dorsales iguales en el mismo equipo, aunque sí en equipos distintos. Los
partidos se juegan por jornadas: cada partido tiene una fecha, una jornada, un equipo local y un
equipo visitante, y los dos equipos tienen que ser distintos. De cada partido se quiere registrar
gol a gol quién marcó y en qué minuto, en el orden en que se produjeron: el primer gol del partido,
el segundo… El resultado no se apunta: se cuenta a partir de los goles. Un equipo puede estar
inscrito y no haber jugado todavía. Un jugador puede no haber marcado nunca.

**Preguntas que tiene que contestar:**

1. ¿Qué resultado tuvo un partido?
2. ¿Quién es el máximo goleador del torneo? ¿Y de cada equipo?
3. ¿Qué partidos ha jugado un equipo, como local y como visitante?
4. ¿Qué equipos no han jugado ningún partido?

**Antes de entregar, comprueba:**

- ¿Tu diseño distingue qué equipo jugó en casa?
- Dos equipos se enfrentan en la jornada 2 y otra vez en la final. ¿Caben los dos partidos?
- El dorsal 7 existe en varios equipos. ¿Qué impide en tus tablas que haya dos 7 en el mismo?
- Un jugador marca dos goles en el mismo partido. ¿Caben los dos?
- ¿Qué identifica a un gol? ¿Tiene sentido «el gol número 3» sin decir de qué partido?
- Pregunta 1: ¿de dónde sale el resultado si no lo guardas?
- Lista D: hay al menos tres reglas del enunciado o del sentido común que ni el diagrama ni las
  tablas garantizan.

---

## Entrega

Un único documento con los cuatro ejercicios, cada uno con sus partes A, B, C y D. Fecha y forma de
entrega, las que diga el profesor.

Si en un ejercicio dudas entre dos opciones (atributo o entidad, clave natural o subrogada), elige
una y escribe en una línea por qué. Una decisión justificada vale más que la «correcta» sin
justificar.

---

Última actualización: 25 de septiembre de 2026.
