# GBD · Ejercicios E/R 3 · G1 · Plataforma de vídeo

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

> Una plataforma de vídeo tiene cuentas de suscripción: de cada una, email, contraseña, plan
> (básico, estándar, prémium), fecha de alta y dirección de facturación (calle, código postal,
> ciudad). Cada cuenta tiene hasta cinco perfiles, que se distinguen por su nombre **dentro de la
> cuenta**: dos cuentas distintas pueden tener un perfil «Peques».
>
> Del catálogo, de todos los contenidos se guarda título, año, edad mínima recomendada y los
> idiomas de audio disponibles. Cada contenido es una película, de la que interesa la duración,
> o una serie. Las series tienen temporadas numeradas (1, 2, 3…) y cada temporada, episodios
> numerados con su título y duración.
>
> Se registra qué ve cada perfil: qué película o qué episodio, cuándo empezó a verlo y hasta qué
> minuto llegó. Además, un perfil puede seguir a otros perfiles, de cualquier cuenta, para ver lo
> que recomiendan.

## Preguntas que tiene que contestar

1. ¿Qué episodios de *una serie dada* ha visto un perfil, y hasta qué minuto?
2. ¿A quién sigue un perfil y quién le sigue a él?
3. ¿Qué contenidos tienen audio en euskera?
4. ¿Cuántas temporadas tiene cada serie?
