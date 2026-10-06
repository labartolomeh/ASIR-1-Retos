# GBD · Ejercicios E/R 3 · G2 · Empresa de desarrollo de software

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

> Una empresa de desarrollo organiza a sus empleados en departamentos; cada empleado está en uno.
> Cada departamento tiene un director, que es uno de sus empleados, aunque el puesto puede estar
> vacante una temporada. Todos los empleados, menos la consejera delegada, tienen un responsable
> directo, que es otro empleado. De cada empleado: nombre, email de la empresa y fecha de alta.
>
> Algunos empleados son técnicos (de ellos, nivel —júnior, sénior— y especialidad) y otros
> comerciales (porcentaje de comisión y zona). Los de administración y dirección no son ni una cosa
> ni otra.
>
> La empresa tiene portátiles con número de inventario, modelo y fecha de compra. Cada empleado
> tiene como mucho uno asignado, y hay portátiles de reserva sin asignar.
>
> Los proyectos se hacen para clientes: de cada cliente, razón social, CIF y una persona de
> contacto con su nombre, teléfono y email. Cada proyecto es de un cliente y tiene fechas de inicio
> y fin. En un proyecto trabajan varios empleados, cada uno con un rol y unas horas por semana.
> Además se quiere saber qué tecnologías usa cada empleado **en cada proyecto**: en la web de
> Bodegas Aragón, Ana usa PHP y Docker, y Luis solo SQL; en otro proyecto, Ana usa solo Python.

## Preguntas que tiene que contestar

1. ¿Quién depende, directa o indirectamente, de un empleado dado?
2. ¿Qué empleados han usado Docker, y en qué proyectos?
3. ¿Qué portátiles están sin asignar?
4. ¿Cuántas horas semanales tiene comprometidas cada empleado entre todos sus proyectos?
5. ¿Qué departamentos no tienen director ahora mismo?
