# Píldora 1 — Anatomía de un PC

## Objetivo

Al terminar esta píldora, el alumnado debería ser capaz de:

- Identificar los principales componentes de un ordenador y explicar su función básica.
- Reconocer los elementos, conectores y zonas principales de una placa base.
- Distinguir qué elementos son imprescindibles para que un equipo realice el POST y arranque.
- Relacionar unos componentes con otros.
- Localizar la marca, el modelo y la revisión de un componente.
- Buscar y utilizar documentación técnica del fabricante.
- Manipular y documentar un equipo siguiendo unas normas básicas de seguridad.

> [!important]
> El objetivo no es memorizar todos los componentes, sockets o conectores existentes, sino aprender a **identificarlos, investigar y justificar las conclusiones**.

---

# 1. Seguridad antes de manipular un equipo

Antes de abrir o manipular un ordenador:

1. Apagar correctamente el equipo.
2. Desconectar el cable de alimentación y los periféricos.
3. Pulsar durante unos segundos el botón de encendido para ayudar a descargar la energía residual.
4. Trabajar sobre una superficie estable, limpia y bien iluminada.
5. Descargar la electricidad estática tocando una superficie metálica conectada a tierra o utilizar una pulsera ESD cuando proceda.
6. Manipular placas y tarjetas por los bordes, evitando tocar contactos y componentes electrónicos.
7. No forzar conectores, módulos ni tornillos.
8. Fotografiar las conexiones antes de desmontar.
9. Mantener tornillos y piezas pequeñas ordenados.

> [!danger]
> Nunca debemos abrir una fuente de alimentación ni un monitor. Pueden mantener cargas eléctricas peligrosas incluso estando desconectados.

> [!warning]
> Antes de retirar un disipador hay que comprobar cómo está fijado. Al volver a instalarlo será necesario revisar o renovar la pasta térmica.

---

# 2. ¿Qué necesita un ordenador para funcionar?

Un ordenador no es una única pieza, sino un sistema de componentes que trabajan coordinadamente.

```text
ENTRADA
  ↓
CPU ↔ RAM
  ↓
ALMACENAMIENTO
  ↓
SALIDA
```

Para que todo esto funcione necesitamos además una placa base que conecte los componentes y una fuente de alimentación que les proporcione energía.

Los componentes básicos que podemos encontrar en un PC son:

- Placa base.
- Procesador o CPU.
- Memoria RAM.
- Almacenamiento.
- Fuente de alimentación.
- Sistema de refrigeración.
- Tarjeta gráfica, si es necesaria.
- Tarjetas de expansión.
- Caja y periféricos.

---

# 3. Placa base

La **placa base** es el componente principal sobre el que se conectan y comunican el resto de elementos. Sirve de soporte físico, distribuye alimentación y contiene parte de la electrónica y el firmware necesarios para iniciar el equipo.

## 3.1. Formato de la placa

El formato determina, entre otras cosas, el tamaño de la placa, su fijación a la caja y el número aproximado de ranuras disponibles.

Formatos habituales:

- **ATX**.
- **microATX**.
- **Mini-ITX**.
- **E-ATX**, en algunos equipos de mayores dimensiones.

> [!important]
> La compatibilidad no es solo electrónica: la placa debe caber en la caja y coincidir con sus puntos de anclaje.

## 3.2. Socket del procesador

Es el lugar donde se instala la CPU. Cada socket está diseñado para determinadas familias de procesadores.

```text
Intel LGA1150
Intel LGA1151
AMD AM4
AMD AM5
```

> [!warning]
> Que un procesador encaje físicamente no garantiza que sea compatible. También hay que comprobar el chipset, la versión de BIOS/UEFI y la lista de CPU admitidas por el fabricante.

## 3.3. Ranuras de memoria RAM

Son los conectores en los que instalamos los módulos de memoria. Suelen estar cerca del procesador.

```text
DIMM_A1
DIMM_A2
DIMM_B1
DIMM_B2
```

Estas referencias ayudan a instalar correctamente los módulos cuando queremos utilizar varios canales de memoria. El manual indica qué ranuras debemos ocupar primero.

## 3.4. Chipset

El **chipset** gestiona distintas comunicaciones y funciones de la placa. Dependiendo de la generación puede intervenir en:

- Puertos USB.
- Conexiones SATA.
- Líneas PCI Express.
- Red y audio integrados.
- Otros dispositivos de entrada y salida.

En los equipos modernos, muchas funciones que antes dependían del chipset se han integrado en la CPU.

## 3.5. VRM: alimentación del procesador

El **VRM** (*Voltage Regulator Module*) convierte y estabiliza la tensión que necesita la CPU. Esta zona suele estar alrededor del socket y se reconoce por la presencia de:

- Bobinas.
- MOSFET.
- Condensadores.
- Disipadores metálicos, en algunas placas.

## 3.6. Condensadores

Los condensadores participan en el filtrado eléctrico y la estabilización de tensiones. En placas antiguas pueden aparecer condensadores hinchados, deformados o con fugas, lo que puede provocar inestabilidad o impedir el arranque.

> [!warning]
> La inspección debe ser visual. No debemos tocar ni intentar descargar componentes electrónicos.

## 3.7. BIOS, UEFI y chip de firmware

La placa contiene un firmware que inicia y configura el hardware al encender el equipo.

- En los equipos antiguos se utilizaba principalmente **BIOS**.
- En los modernos se utiliza normalmente **UEFI**.

Desde su configuración podemos:

- Consultar el procesador y la memoria detectados.
- Comprobar unidades de almacenamiento.
- Consultar temperaturas y controlar ventiladores.
- Activar o desactivar dispositivos integrados.
- Configurar fecha y hora.
- Seleccionar el orden y el modo de arranque.
- Activar funciones como virtualización o arranque seguro, si están disponibles.

El firmware se almacena en un pequeño chip de memoria no volátil. Históricamente se utilizaron memorias **EPROM** y **EEPROM**; en las placas modernas suele emplearse memoria **Flash**, que permite actualizar el firmware mediante software.

> [!note]
> Aunque se hable de «chip de BIOS», en una placa moderna normalmente se trata de una memoria Flash que almacena el firmware UEFI.

> [!warning]
> Una actualización de firmware interrumpida o realizada con un archivo incorrecto puede dejar la placa sin arrancar. No debe actualizarse sin una necesidad y un procedimiento claros.

## 3.8. Pila y configuración CMOS

Muchas placas incluyen una pila de botón, normalmente **CR2032**. Ayuda a mantener el reloj y determinados parámetros cuando el equipo está desconectado.

Una pila agotada puede provocar:

- Pérdida de fecha y hora.
- Avisos al encender.
- Pérdida de determinadas configuraciones del firmware.

Todavía se utilizan expresiones como **borrar CMOS**, **reset CMOS** o **clear CMOS** para referirse a restaurar la configuración del firmware. La placa puede incluir pines o un botón con nombres como:

```text
CLR_CMOS
CLRTC
JBAT1
```

> [!warning]
> Antes de realizar un borrado de CMOS debemos consultar el manual y desconectar la alimentación.

## 3.9. Conectores de alimentación

### Alimentación principal

La placa recibe la alimentación principal mediante un conector **ATX de 24 pines**. En placas antiguas puede ser de 20 pines.

### Alimentación de CPU

La CPU dispone de un conector de alimentación específico, situado normalmente cerca del socket:

```text
4 pines
8 pines
4 + 4 pines
```

> [!warning]
> Es frecuente olvidar la alimentación de CPU durante un montaje. Los conectores de CPU y PCIe pueden parecerse, pero no deben intercambiarse.

## 3.10. Conectores de almacenamiento

### SATA

Los conectores SATA se utilizan para HDD, SSD SATA y unidades ópticas. Pueden estar identificados como `SATA0`, `SATA1`, `SATA2`…

```text
Cable SATA de datos → placa base
Cable SATA de alimentación → fuente de alimentación
```

### M.2

Las placas modernas pueden incluir conectores M.2, utilizados principalmente para SSD:

- M.2 SATA.
- M.2 NVMe mediante PCI Express.

> [!warning]
> M.2 describe principalmente un formato físico. No toda unidad M.2 es compatible con cualquier ranura M.2: hay que comprobar interfaz, llave, longitud admitida y posibles limitaciones compartidas con SATA o PCIe.

## 3.11. Ranuras de expansión

Las ranuras **PCI Express** permiten instalar tarjetas de expansión.

```text
PCIe x1
PCIe x4
PCIe x8
PCIe x16
```

Ejemplos:

- Tarjeta gráfica.
- Tarjeta de red o Wi-Fi.
- Tarjeta de sonido.
- Controladora SATA o USB.
- Adaptador para almacenamiento NVMe.

La ranura PCIe x16 suele utilizarse para la tarjeta gráfica. En placas antiguas podemos encontrar también PCI o AGP.

## 3.12. Conectores para ventiladores

La placa puede alimentar y controlar ventiladores mediante conectores como:

```text
CPU_FAN
CPU_OPT
SYS_FAN
CHA_FAN
```

El ventilador del disipador del procesador debe conectarse normalmente a `CPU_FAN`.

## 3.13. Conectores del panel frontal

Los botones y pilotos de la caja se conectan a un grupo de pines que puede llamarse:

```text
F_PANEL
PANEL
JFP1
```

En él solemos conectar:

```text
POWER SW
RESET SW
POWER LED
HDD LED
```

La distribución depende de cada modelo, por lo que debemos consultar el manual. Los interruptores no suelen tener polaridad; los LED sí.

## 3.14. USB y audio frontales

Los puertos frontales de la caja se conectan a cabeceras internas diferentes:

- USB 2.0.
- USB 3.x.
- USB-C frontal.
- Audio frontal, identificado como `HD_AUDIO`, `AAFP` o `JAUD1`.

No debemos forzar un conector ni desplazarlo una fila de pines.

## 3.15. Controladoras integradas

Muchas placas incorporan:

- **Controladora de audio**, frecuentemente de fabricantes como Realtek.
- **Controladora de red Ethernet**, de fabricantes como Intel, Realtek o Broadcom.
- En algunos modelos, conectividad Wi-Fi y Bluetooth.
- Controladoras adicionales para USB, SATA u otras funciones.

## 3.16. Puertos traseros

| Función | Conectores frecuentes |
|---|---|
| USB | USB-A, USB-C; distintas versiones y velocidades |
| Red | RJ45 Ethernet; conectores para antenas Wi-Fi en algunos modelos |
| Vídeo | VGA, DVI, HDMI, DisplayPort |
| Audio | Minijack de 3,5 mm y, en algunos modelos, audio digital |
| Periféricos antiguos | PS/2 para teclado o ratón |

> [!important]
> Que la placa disponga de HDMI o DisplayPort no garantiza que esa salida produzca imagen. Cuando la salida depende de la CPU, el procesador instalado debe incluir gráficos integrados.

## 3.17. Referencias visuales

Estas imágenes y guías sirven como apoyo. La distribución de los componentes cambia entre fabricantes, generaciones y formatos.

- [Placa moderna con sus zonas y componentes principales — Overclockers UK](https://www.overclockers.co.uk/blog/anatomy-of-a-motherboard-everything-you-need-to-know/)
- [Placa ATX antigua con componentes numerados — Wikimedia Commons](https://commons.wikimedia.org/wiki/File:MSI_KT3_Ultra_ver_1.0_-_labeled.jpg)
- [Esquema general de componentes de una placa base — Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Motherboard_Components.svg)
- [Guía de conexión del panel frontal — Corsair](https://www.corsair.com/us/en/explorer/diy-builder/cases/how-do-i-connect-the-front-panel-connectors-to-my-motherboard/)

> [!note]
> La placa MSI del segundo enlace es antigua y utiliza AGP, PCI y ATA. Es útil para comparar la evolución del hardware, no como plantilla de una placa actual.

### Reto visual

Comparad vuestra placa con las imágenes y localizad en ella los elementos equivalentes. No tienen por qué estar en el mismo lugar.

---

# 4. Procesador — CPU

La **CPU** ejecuta las instrucciones de los programas.

Características importantes:

- Fabricante y modelo.
- Número de núcleos e hilos.
- Frecuencia.
- Socket.
- Consumo o TDP.
- Gráfica integrada, en algunos modelos.

```text
Ejemplo: Intel Core i5-6500
4 núcleos
Socket LGA1151
```

La compatibilidad depende de varios elementos:

```text
CPU → socket → chipset → versión de BIOS/UEFI → placa base
```

---

# 5. Memoria RAM

La **RAM** almacena temporalmente los datos y programas que el procesador está utilizando. Es rápida pero volátil: al apagar el equipo, su contenido desaparece.

Características principales:

- Tipo: DDR3, DDR4, DDR5…
- Capacidad: 4 GB, 8 GB, 16 GB…
- Frecuencia o velocidad indicada.
- Formato:
  - DIMM: normalmente, ordenadores de sobremesa.
  - SO-DIMM: normalmente, portátiles y equipos compactos.

> [!important]
> Una placa diseñada para DDR4 no puede utilizar módulos DDR3 o DDR5. Aunque se parezcan, la posición de la muesca y sus características eléctricas son diferentes.

---

# 6. Almacenamiento

El almacenamiento conserva los datos incluso cuando apagamos el ordenador.

## HDD

Disco mecánico de gran capacidad y bajo coste por gigabyte, pero más lento y con partes móviles.

## SSD SATA

Utiliza memoria Flash, no tiene partes móviles y suele ser mucho más rápido que un HDD. Se comunica mediante SATA.

## SSD NVMe

Utiliza memoria Flash y se comunica mediante PCI Express. Es habitual encontrarlo en formato M.2.

> [!warning]
> No debemos utilizar «M.2» y «NVMe» como si fueran sinónimos. M.2 es un formato; una unidad M.2 puede usar SATA o PCIe/NVMe.

---

# 7. Fuente de alimentación — PSU

La **fuente de alimentación** transforma la corriente de la red eléctrica en las tensiones que necesitan los componentes.

Características importantes:

- Potencia total en vatios.
- Calidad y eficiencia.
- Conectores disponibles.
- Intensidad disponible en las distintas líneas.

```text
ATX 24 pines → placa base
CPU 4/8 pines → alimentación del procesador
SATA → discos y otros dispositivos
PCIe → algunas tarjetas gráficas
```

---

# 8. Tarjeta gráfica — GPU

La GPU se encarga del procesamiento gráfico.

## Integrada

Está incluida en el procesador o, en equipos antiguos, en la propia placa. Reduce coste y consumo y suele ser suficiente para ofimática y muchas tareas de administración.

## Dedicada

Es una tarjeta independiente conectada normalmente mediante PCI Express. Algunos modelos necesitan alimentación adicional desde la fuente.

---

# 9. Refrigeración

El procesador y otros componentes generan calor. Para disiparlo se utilizan disipadores, ventiladores, pasta térmica y, en algunos equipos, refrigeración líquida.

```text
CPU → pasta térmica → disipador → ventilador
```

La pasta térmica rellena pequeñas irregularidades y mejora la transferencia de calor. No sustituye al disipador ni debe aplicarse en cantidad excesiva.

---

# 10. Tarjetas de expansión y periféricos

Las tarjetas de expansión añaden funciones mediante PCI Express. Los periféricos permiten comunicarnos con el ordenador o ampliar sus funciones.

| Tipo | Ejemplos |
|---|---|
| Entrada | Teclado, ratón, micrófono, cámara |
| Salida | Monitor, altavoces, impresora |
| Entrada y salida | Tarjeta de red, memoria USB, pantalla táctil |

---

# 11. BIOS/UEFI, POST y secuencia de arranque

Al pulsar el botón de encendido no se carga inmediatamente el sistema operativo:

```text
Encendido
  ↓
La fuente y la placa reciben la orden de arrancar
  ↓
La CPU comienza a ejecutar el firmware BIOS/UEFI
  ↓
POST: comprobaciones iniciales del hardware
  ↓
Detección de RAM, almacenamiento y otros dispositivos
  ↓
Selección del dispositivo de arranque
  ↓
Cargador de arranque
  ↓
Sistema operativo
```

El **POST** (*Power-On Self-Test*) es el conjunto de comprobaciones iniciales. Si encuentra un problema, puede comunicarlo mediante:

- Mensajes en pantalla.
- Pitidos del altavoz interno.
- LED de diagnóstico, por ejemplo `CPU`, `DRAM`, `VGA` o `BOOT`.
- Códigos en un visor POST.
- Patrones luminosos propios del fabricante.

> [!important]
> El significado de los pitidos, LED y códigos depende del fabricante y del modelo. Hay que consultar su documentación.

---

# 12. Componentes imprescindibles y montaje mínimo

Para que un ordenador realice el POST necesitamos normalmente:

```text
Placa base
+ CPU con disipador
+ al menos un módulo de RAM
+ fuente de alimentación
```

Además, necesitaremos un sistema gráfico para obtener imagen. Para cargar un sistema operativo necesitaremos también un medio de arranque: SSD, HDD, USB, red…

Un equipo puede completar el POST sin un disco con sistema operativo, pero no podrá cargarlo. Sin RAM o sin CPU, normalmente no completará el POST.

## Montaje mínimo para diagnóstico

Para descartar componentes, podemos probar una configuración mínima:

- Placa base.
- CPU y disipador.
- Un único módulo de RAM en la ranura indicada por el manual.
- Fuente con ATX y alimentación de CPU conectados.
- GPU solo si no disponemos de gráficos integrados funcionales.
- Monitor y, cuando sea necesario, teclado.

Después se añaden, uno a uno, almacenamiento, módulos de RAM, tarjetas y periféricos.

> [!warning]
> Estas pruebas deben realizarse de forma controlada y evitando cortocircuitos. No se apoyará la placa directamente sobre una superficie conductora.

---

# 13. Herramientas básicas

Según la tarea, pueden ser útiles:

- Destornilladores adecuados.
- Linterna.
- Recipiente o clasificador para tornillos.
- Bridas reutilizables.
- Pulsera o medidas de protección ESD.
- Alcohol isopropílico y material que no deje residuos.
- Pasta térmica.
- Multímetro o tester de fuente, si se conoce su uso seguro.
- Memoria USB de arranque con herramientas autorizadas.
- Cámara o teléfono para documentar conexiones y etiquetas.

> [!important]
> Una herramienta solo debe utilizarse cuando conocemos su función y el procedimiento. El multímetro no se empleará directamente sobre la red eléctrica ni se abrirá la fuente.

---

# 14. Cómo enfrentarnos a un componente desconocido

Durante el reto aparecerán componentes que no conocemos. No debemos adivinar qué son.

## Paso 1 — Identificar

Buscar:

- Fabricante.
- Modelo exacto.
- Revisión de hardware.
- Referencia o *part number*.
- Número de serie.
- Etiquetas y serigrafía.

> [!note]
> El **modelo** identifica un tipo de producto. El **número de serie** suele identificar una unidad concreta. No deben confundirse.

## Paso 2 — Buscar documentación

1. Página del fabricante.
2. Manual técnico.
3. Ficha técnica o *datasheet*.
4. Lista oficial de componentes compatibles.
5. Documentación de distribuidores fiables.
6. Otras fuentes contrastadas.

## Paso 3 — Extraer la información necesaria

```text
Fabricante:
Modelo:
Revisión:
Formato:
Socket:
Chipset:
CPU compatibles:
Versión de BIOS/UEFI necesaria:
Tipo y capacidad máxima de RAM:
Número de ranuras RAM:
Puertos SATA:
Conectores M.2:
Ranuras PCIe:
Conectores internos:
Puertos traseros:
Fuente de la información:
```

## Paso 4 — Documentar la fuente

No basta con afirmar «esta RAM sirve». Debemos poder justificarlo: «Según el manual del fabricante, la placa admite memoria DDR4 hasta…».

## No memorices: investiga

```text
Observar → identificar → buscar → contrastar → probar → documentar
```

---

# 15. Compatibilidad: tres preguntas diferentes

| Tipo de compatibilidad | Pregunta |
|---|---|
| Física | ¿Encaja y cabe correctamente? |
| Eléctrica | ¿Utiliza la alimentación, tensión y conectores adecuados? |
| Lógica | ¿La placa, el chipset, el firmware y el sistema reconocen y admiten el componente? |

Relaciones que debemos investigar:

```text
CPU ↔ socket ↔ chipset ↔ BIOS/UEFI
Placa base ↔ tipo y capacidad de RAM
Placa base ↔ interfaz de almacenamiento
Placa base ↔ tarjetas de expansión
Placa base ↔ formato de caja
Fuente ↔ potencia, consumo y conectores
```

---

# 16. Documentación mediante fotografías

Antes y durante el desmontaje realizaremos, cuando esté permitido:

1. Una foto general del interior.
2. Una foto de la marca, modelo y número de inventario del equipo.
3. Una foto legible de cada etiqueta relevante.
4. Una foto de las conexiones antes de retirarlas.
5. Una foto final que permita comprobar el montaje.

Las imágenes deben estar enfocadas, mostrar solo la información necesaria y tener un nombre reconocible. Debemos evitar difundir números de serie, datos personales o información sensible fuera del entorno autorizado.

```text
EQ03_vista_general_antes.jpg
EQ03_placa_modelo.jpg
EQ03_conexiones_panel_frontal.jpg
EQ03_vista_general_despues.jpg
```

---

>[!Tip]
>Preguntas que debéis poder responder
>1. ¿Dónde está conectado el almacenamiento?
>2. ¿Cuántas ranuras RAM hay y cuántas están ocupadas?
>3. ¿Queda algún conector SATA libre?
>4. ¿Tiene ranura M.2? ¿Qué tipos de unidad admite?
>5. ¿Cómo sabemos qué CPU admite la placa?
>6. ¿Qué conectores de alimentación utiliza?
>7. ¿Podría realizar el POST sin almacenamiento? ¿Qué ocurriría después?
>8. ¿Podría completar el POST sin RAM?
>9. ¿Cómo sabemos si la gráfica es integrada o dedicada?
>10. ¿Qué datos hemos confirmado mediante el manual y cuáles proceden de la observación?

---

# 18. Pregunta final

> **Si encontramos una CPU, una placa base y varios módulos de RAM sueltos, ¿cómo podemos determinar cuáles son compatibles entre sí y justificarlo con documentación técnica?**


---

## Resumen

```text
PLACA BASE
│
├── CPU
├── RAM
├── ALMACENAMIENTO
├── GPU
├── TARJETAS DE EXPANSIÓN
└── PERIFÉRICOS

FUENTE DE ALIMENTACIÓN
└── proporciona energía al conjunto

BIOS/UEFI
└── inicia, comprueba y configura el hardware
```

Ideas clave:

- El ordenador es un sistema formado por componentes relacionados.
- La placa base conecta, alimenta y permite comunicarse a muchos de ellos.
- No todos los componentes son compatibles física, eléctrica y lógicamente.
- No necesitamos memorizar miles de modelos y conectores.
- Debemos identificar cada componente y consultar documentación fiable.
- Las fotografías y observaciones deben permitir reconstruir el trabajo realizado.
- Toda decisión de compatibilidad o diagnóstico debe poder justificarse.
