# Píldora 2 — Compatibilidad entre componentes

## Enfoque de esta píldora

Esta segunda píldora parte de una pregunta que debería aparecer de forma natural durante el reto:

> **Tenemos una placa base, varias CPU, varios módulos de RAM y varios discos. ¿Cómo sabemos qué componentes podemos montar juntos?**

La idea no es memorizar generaciones, sockets o modelos concretos, sino aprender un **método de comprobación de compatibilidad**.

---

# 1. Objetivos

Al terminar esta píldora, el alumnado debería ser capaz de:

- Identificar qué factores determinan la compatibilidad entre componentes.
- Comprobar si una CPU es compatible con una placa base.
- Comprobar si una memoria RAM es compatible con una placa.
- Diferenciar compatibilidad física de compatibilidad funcional.
- Distinguir SATA, M.2 SATA y M.2 NVMe.
- Interpretar de forma básica las ranuras PCI Express.
- Comprobar si una fuente de alimentación es adecuada.
- Consultar documentación técnica para justificar una decisión.

---

# 2. Idea clave: que encaje no significa que sea compatible

Hay varios niveles de compatibilidad.

## Compatibilidad física

El componente puede conectarse físicamente.

Ejemplos:

- Una CPU entra en el socket.
- Una tarjeta entra en una ranura PCIe.
- Un módulo RAM entra en su ranura.

## Compatibilidad eléctrica

Las tensiones, alimentación y señales son compatibles.

## Compatibilidad lógica o funcional

La placa, firmware o sistema reconoce correctamente el componente.

## Compatibilidad de firmware

Puede ser necesario que la BIOS/UEFI tenga soporte para ese componente.

> [!important]
> Un componente puede ser físicamente compatible y, aun así, no funcionar.

---

# 3. CPU y placa base

Esta es una de las compatibilidades más importantes.

Debemos comprobar:

```text
CPU
↓
Socket
↓
Chipset
↓
BIOS/UEFI
↓
Placa base
```

---

## 3.1 Socket

El socket es el sistema físico y eléctrico mediante el que se conecta la CPU a la placa base.

Ejemplos habituales:

### Intel

- LGA1150
- LGA1151
- LGA1200
- LGA1700
- LGA1851

### AMD

- AM3+
- AM4
- AM5

Dos procesadores con sockets distintos no son compatibles.

Ejemplo:

```text
CPU Intel LGA1151
+
Placa LGA1200

→ NO compatible
```

Pero compartir socket tampoco garantiza siempre la compatibilidad.

---

# 4. El chipset

El **chipset** es un conjunto de controladores de la placa base que determina muchas de sus capacidades.

Puede afectar a:

- Familias de CPU soportadas.
- Número de líneas PCIe.
- Número de puertos USB.
- Puertos SATA.
- Posibilidades de overclocking.
- Soporte de almacenamiento.
- Otras funciones de la placa.

Ejemplo simplificado:

```text
Mismo socket
≠
compatibilidad automática
```

Una CPU puede utilizar el mismo socket físico que otra pero requerir un chipset diferente o una versión de BIOS determinada.

---

# 5. BIOS/UEFI y compatibilidad de CPU

Incluso si:

- socket coincide;
- chipset es compatible;

la CPU puede no funcionar si la BIOS no incluye soporte para ella.

Esto ocurre especialmente cuando:

- una placa sale al mercado antes que una nueva generación de CPU;
- el fabricante añade compatibilidad mediante una actualización posterior.

Por eso, al comprobar una CPU concreta, lo más fiable es buscar:

> **CPU Support List**

en la página del fabricante de la placa.

Ejemplo:

```text
Placa: ASUS B450-PLUS
CPU: Ryzen X

1. Buscar modelo exacto de placa.
2. Ir a soporte.
3. Buscar CPU Support.
4. Comprobar si aparece la CPU.
5. Comprobar versión mínima de BIOS.
```

---

# 6. Método para comprobar CPU + placa

## Paso 1

Identificar modelo exacto de la CPU.

Ejemplo:

```text
Intel Core i5-6500
```

## Paso 2

Identificar modelo exacto de placa.

Ejemplo:

```text
Gigabyte GA-B150M-D3H
```

## Paso 3

Consultar:

- socket de la CPU;
- socket de la placa.

## Paso 4

Consultar la lista de CPU soportadas por la placa.

## Paso 5

Comprobar si requiere una BIOS concreta.

## Conclusión

Documentar:

```text
Compatible: Sí / No
Motivo:
Fuente:
Versión BIOS necesaria:
```

---

# 7. Memoria RAM

Para comprobar la compatibilidad de la RAM debemos analizar varios factores.

```text
Tipo
+
Formato
+
Capacidad
+
Frecuencia
+
Número de módulos
+
Compatibilidad placa/CPU
```

---

# 8. Tipo de RAM

Actualmente podemos encontrar:

- DDR
- DDR2
- DDR3
- DDR4
- DDR5

Estas generaciones **no son intercambiables**.

Por ejemplo:

```text
Placa DDR4
+
RAM DDR3

→ NO compatible
```

Los módulos tienen una muesca en diferente posición para evitar montajes incorrectos.

> [!warning]
> Nunca se debe forzar un módulo de RAM en una ranura.

---

# 9. DIMM y SO-DIMM

También debemos distinguir el formato.

## DIMM

Habitual en equipos de sobremesa.

## SO-DIMM

Habitual en portátiles y algunos mini-PC.

Un SO-DIMM no puede instalarse directamente en una ranura DIMM estándar.

---

# 10. Frecuencia de RAM

Ejemplos:

```text
DDR4-2133
DDR4-2666
DDR4-3200
```

Una memoria más rápida puede funcionar a una frecuencia inferior si la placa o la CPU no soportan la frecuencia máxima del módulo.

Ejemplo simplificado:

```text
RAM DDR4-3200
Placa soporta DDR4-2666

→ Puede funcionar a 2666 MHz
```

Pero hay que consultar documentación porque existen excepciones y limitaciones.

---

# 11. Capacidad máxima

Las placas suelen tener límites como:

```text
4 ranuras
Máximo total: 64 GB
Máximo por módulo: 16 GB
```

Por tanto:

```text
4 × 16 GB = 64 GB
```

puede ser válido.

Pero:

```text
4 × 32 GB = 128 GB
```

no necesariamente lo será.

---

# 12. Canales de memoria

Muchas placas utilizan arquitectura:

- Single Channel.
- Dual Channel.
- Quad Channel.

En un equipo habitual de sobremesa encontraremos frecuentemente **Dual Channel**.

Para aprovecharlo suele ser recomendable instalar módulos iguales o equivalentes en las ranuras indicadas por el fabricante.

Ejemplo:

```text
2 módulos de 8 GB
```

pueden rendir mejor correctamente distribuidos que:

```text
1 módulo de 16 GB
```

aunque la capacidad total sea la misma.

---

# 13. Mezclar memorias RAM

Puede funcionar mezclar:

- distinta marca;
- distinta frecuencia;
- distinta capacidad;

pero no siempre es recomendable.

El sistema suele adaptarse al módulo más lento.

Ejemplo:

```text
DDR4-3200
+
DDR4-2666
```

pueden trabajar ambas a:

```text
2666 MHz
```

Pero pueden aparecer problemas de estabilidad.

Para un entorno docente o profesional:

> Mejor utilizar módulos equivalentes siempre que sea posible.

---

# 14. QVL de memoria

Algunas placas publican una lista denominada:

> **QVL — Qualified Vendor List**

Contiene módulos que el fabricante ha probado.

Esto no significa que:

> “Si no aparece en la lista, no funciona.”

Significa:

> “Estos módulos concretos han sido probados oficialmente.”

---

# 15. Almacenamiento

Aquí podemos encontrar varios estándares.

## HDD SATA

Conexión:

```text
SATA datos
+
SATA alimentación
```

## SSD SATA 2,5"

Utiliza los mismos tipos de conexión que un disco SATA.

## M.2

Aquí aparece una confusión habitual.

> **M.2 no define por sí solo el protocolo.**

Un dispositivo M.2 puede ser:

- SATA.
- PCIe / NVMe.

---

# 16. M.2 SATA frente a M.2 NVMe

Dos unidades pueden parecer prácticamente iguales.

Ejemplo:

```text
SSD M.2 SATA
SSD M.2 NVMe
```

pero utilizan protocolos diferentes.

Antes de montar una unidad debemos comprobar qué admite la placa.

Por ejemplo:

```text
M.2 Socket 3
Supports SATA and PCIe x4
```

sería compatible con ambos.

Pero otra placa puede indicar:

```text
M.2 PCIe only
```

y entonces una unidad M.2 SATA no funcionaría.

---

# 17. Key de M.2

Los módulos M.2 pueden presentar diferentes muescas.

Ejemplos:

- B-Key.
- M-Key.
- B+M-Key.

Esto aporta información sobre compatibilidad física y posibles interfaces.

Sin embargo:

> No debemos decidir únicamente mirando la muesca.

Hay que consultar la especificación del dispositivo y la placa.

---

# 18. Tamaño físico M.2

También existen diferentes longitudes.

Ejemplos:

```text
2230
2242
2260
2280
22110
```

El código indica:

```text
22 mm de ancho
80 mm de largo
```

para un 2280.

La placa debe disponer del punto de fijación adecuado.

---

# 19. SATA

SATA ha tenido varias generaciones:

- SATA I.
- SATA II.
- SATA III.

Normalmente existe compatibilidad hacia atrás.

Ejemplo:

```text
SSD SATA III
+
Puerto SATA II

→ funciona, pero limitado a la velocidad de SATA II
```

---

# 20. PCI Express

PCI Express se utiliza para:

- GPU.
- Tarjetas de red.
- Controladoras.
- Capturadoras.
- SSD NVMe.
- Otros dispositivos.

Podemos encontrar ranuras:

```text
PCIe x1
PCIe x4
PCIe x8
PCIe x16
```

---

# 21. Tamaño físico y líneas PCIe

Una ranura física x16 no significa necesariamente que utilice 16 líneas eléctricas.

Por ejemplo:

```text
PCIe x16 físico
PCIe x4 eléctrico
```

Esto es frecuente en algunas placas.

Por tanto debemos distinguir:

- Tamaño físico.
- Número de líneas realmente disponibles.

---

# 22. Versiones PCI Express

Ejemplos:

- PCIe 2.0
- PCIe 3.0
- PCIe 4.0
- PCIe 5.0

Existe, en general, compatibilidad entre generaciones.

Ejemplo:

```text
Tarjeta PCIe 4.0
+
Ranura PCIe 3.0
```

puede funcionar, pero limitada por la velocidad de PCIe 3.0.

---

# 23. Tarjeta gráfica y compatibilidad

Para montar una GPU debemos comprobar:

- Ranura PCIe disponible.
- Espacio físico en la caja.
- Potencia de la fuente.
- Conectores de alimentación.
- Compatibilidad con firmware si se trata de equipos antiguos.
- Posible cuello de botella, aunque esto ya es una cuestión de rendimiento más que de compatibilidad.

---

# 24. Fuente de alimentación

La fuente debe ser compatible en varios sentidos.

## Potencia

Debe proporcionar suficiente potencia.

Ejemplo:

```text
CPU: 65 W
GPU: 200 W
Resto del sistema: ~100 W
```

No elegiríamos una fuente de 250 W.

Pero tampoco basta con mirar solo la potencia total.

---

# 25. Conectores de alimentación

Debemos comprobar que dispone de los conectores necesarios.

Habituales:

```text
ATX 24 pines → placa
EPS 4/8 pines → CPU
PCIe 6/8 pines → GPU
SATA → almacenamiento
Molex → hardware antiguo
```

Una fuente puede tener suficiente potencia y no tener el conector requerido.

---

# 26. Formato de la fuente

Ejemplos:

- ATX.
- SFX.
- TFX.

Debe ser compatible físicamente con la caja.

---

# 27. Calidad de la fuente

Dos fuentes de:

```text
500 W
```

no tienen necesariamente la misma calidad.

Factores:

- Fabricante.
- Protecciones.
- Eficiencia.
- Calidad interna.
- Potencia real en la línea de 12 V.

Para este primer reto no hace falta entrar en profundidad, pero sí dejar claro que:

> **“500 W” no es suficiente información para valorar una fuente.**

---

# 28. Caja y formato de placa

También existe compatibilidad física entre:

- Caja.
- Placa base.
- Fuente.
- GPU.
- Refrigeración.

Formatos habituales de placa:

- ATX.
- Micro-ATX.
- Mini-ITX.

Una caja ATX suele aceptar placas más pequeñas.

Ejemplo:

```text
Caja ATX
→ ATX
→ Micro-ATX
→ Mini-ITX
```

Pero hay que comprobar las especificaciones de la caja.

---

# 29. Refrigeración y CPU

Para montar un disipador debemos comprobar:

- Compatibilidad con el socket.
- Altura máxima admitida por la caja.
- Capacidad térmica.
- Espacio respecto a la RAM.
- Sistema de anclaje.

Un disipador compatible con AM4 no tiene por qué ser directamente compatible con LGA1700.

---

# 30. Compatibilidad no significa rendimiento óptimo

Ejemplo:

```text
CPU moderna
+
GPU muy antigua
```

Puede ser perfectamente compatible.

Pero el resultado puede estar desequilibrado.

Debemos distinguir:

## Compatible

Funciona.

## Adecuado

Tiene sentido para el uso previsto.

## Óptimo

Aprovecha bien el resto del sistema.

---

# 31. Método general para estudiar compatibilidad

Cuando tengamos varios componentes:

## Paso 1 — Identificar exactamente cada pieza

Nunca trabajar con:

```text
"una placa ASUS"
```

Trabajar con:

```text
ASUS PRIME B450M-A II
```

---

## Paso 2 — Buscar documentación oficial

Preferencia:

1. Página del fabricante.
2. Manual.
3. CPU Support List.
4. QVL.
5. Datasheet.

---

## Paso 3 — Crear una matriz de compatibilidad

Ejemplo:

| Componente | Requisito | Componente candidato | ¿Compatible? | Justificación |
|---|---|---|---|---|
| CPU | AM4 | Placa AM4 | Sí | Socket coincidente + CPU Support List |
| RAM | DDR4 | 8 GB DDR4 | Sí | Tipo soportado |
| SSD | M.2 NVMe | M.2 PCIe | Sí | Ranura admite PCIe/NVMe |
| GPU | PCIe x16 | PCIe x16 | Sí | Interfaz compatible |
| PSU | 500 W + PCIe 8 pin | 600 W + PCIe 8 pin | Sí | Potencia y conectores suficientes |

---

# 32. Orden recomendado de comprobación

Para montar un equipo:

```text
1. Placa + CPU
2. Placa + RAM
3. Placa + almacenamiento
4. Placa + GPU/tarjetas
5. Fuente + placa + CPU + GPU
6. Caja + placa + fuente + GPU
7. Refrigeración
```

---

# 33. Preguntas que deberíamos hacernos siempre

## CPU

- ¿Qué socket utiliza?
- ¿Está soportada por esta placa?
- ¿Qué BIOS necesita?

## RAM

- ¿Qué generación DDR utiliza?
- ¿DIMM o SO-DIMM?
- ¿Qué capacidad máxima admite la placa?
- ¿Qué frecuencias admite?

## Disco

- ¿SATA o NVMe?
- ¿El conector M.2 soporta ese protocolo?
- ¿La longitud física es compatible?

## GPU

- ¿Existe ranura PCIe?
- ¿Cabe físicamente?
- ¿Necesita alimentación adicional?
- ¿La fuente puede alimentarla?

## Fuente

- ¿Tiene potencia suficiente?
- ¿Tiene los conectores necesarios?
- ¿Es del formato adecuado?

---

# 34. Errores frecuentes del alumnado

## Error 1

> "La CPU entra, así que sirve."

Incorrecto.

Debe comprobarse:

- socket;
- chipset;
- BIOS;
- lista de compatibilidad.

---

## Error 2

> "Es M.2, por tanto sirve."

Incorrecto.

Hay que comprobar:

- SATA o NVMe;
- key;
- longitud;
- compatibilidad de la ranura.

---

## Error 3

> "La fuente es de 500 W, suficiente."

No necesariamente.

Hay que comprobar:

- consumo;
- conectores;
- calidad;
- formato.

---

## Error 4

> "La RAM es DDR4, por tanto sirve."

No siempre.

Hay que comprobar:

- capacidad;
- frecuencia;
- formato;
- limitaciones de placa y CPU.

---

# 35. Actividad práctica

## Material

Cada grupo debe trabajar con:

- una placa base;
- una CPU;
- varios módulos RAM;
- uno o varios dispositivos de almacenamiento;
- una fuente;
- si existe, alguna tarjeta PCIe.

## Tarea

Determinar qué componentes pueden utilizarse juntos.

Crear una tabla:

| Componente | Modelo exacto | Características relevantes | ¿Compatible? | Fuente consultada |
|---|---|---|---|---|
| Placa base | | | | |
| CPU | | | | |
| RAM 1 | | | | |
| RAM 2 | | | | |
| Disco 1 | | | | |
| Disco 2 | | | | |
| GPU | | | | |
| Fuente | | | | |

---

# 36. Producto final de la actividad

Cada grupo debe proponer una configuración:

```text
Placa:
CPU:
RAM:
Almacenamiento:
GPU:
Fuente:
```

Y justificar:

> **Por qué todos los componentes son compatibles.**

No se aceptará:

> "Porque encajan."

Debe existir una justificación técnica.

---

# 37. Preguntas rápidas para comprobar comprensión

1. ¿Una CPU y una placa con el mismo socket son siempre compatibles?
2. ¿Puede una RAM DDR4-3200 funcionar en una placa limitada a DDR4-2666?
3. ¿Todo SSD M.2 es NVMe?
4. ¿Una GPU PCIe 4.0 puede funcionar en PCIe 3.0?
5. ¿Una fuente de 600 W es automáticamente mejor que una de 500 W?
6. ¿Qué documento consultarías para confirmar que una CPU concreta funciona en una placa?
7. ¿Qué significa que una ranura sea x16 física pero x4 eléctrica?

---

# 38. Resumen visual

```text
CPU
│
├── Socket
├── Chipset
└── BIOS
     ↓
   PLACA
     │
     ├── RAM
     │    ├── DDR
     │    ├── Capacidad
     │    └── Frecuencia
     │
     ├── ALMACENAMIENTO
     │    ├── SATA
     │    └── M.2 SATA / NVMe
     │
     ├── PCIe
     │    └── GPU / expansión
     │
     └── FUENTE
          ├── Potencia
          └── Conectores
```

---

# 39. Qué deberías dominar tú como profesor

Antes de impartir esta píldora conviene que seas capaz de resolver con soltura estos casos:

- Buscar la **CPU Support List** de una placa.
- Identificar un socket a partir del modelo de CPU.
- Identificar qué DDR utiliza una placa.
- Interpretar una especificación como:

```text
4 x DIMM, max 64 GB, DDR4 3200(O.C.) / 2933 / 2666
```

- Diferenciar M.2 SATA y M.2 NVMe.
- Interpretar:

```text
1 x PCIe 3.0 x16
1 x PCIe 2.0 x16 (x4 mode)
```

- Identificar los conectores principales de una fuente.
- Calcular aproximadamente si una fuente es suficiente.
- Buscar el manual técnico de una placa.
- Justificar una compatibilidad con documentación oficial.

---

# 40. Temas que conviene investigar por tu cuenta

No hace falta explicarlos todos en clase, pero sí te conviene tenerlos claros.

## CPU

- Diferencia entre socket y chipset.
- Qué es una generación de CPU.
- Qué significa TDP.
- CPU Support List.
- Actualización de BIOS.

## RAM

- DDR3 / DDR4 / DDR5.
- Frecuencia real frente a frecuencia efectiva.
- Dual Channel.
- QVL.
- XMP / EXPO.
- ECC frente a no ECC.

## Almacenamiento

- SATA.
- AHCI.
- NVMe.
- PCIe.
- M.2.
- Formatos 2230, 2242, 2260, 2280 y 22110.

## PCI Express

- Líneas PCIe.
- Versiones.
- x1 / x4 / x8 / x16.
- Compatibilidad entre generaciones.

## Alimentación

- ATX.
- EPS.
- PCIe 6/8 pines.
- SATA Power.
- Eficiencia 80 PLUS.
- Línea de 12 V.

---

# 41. Qué NO hace falta dominar todavía

Para este primer reto puedes dejar para más adelante:

- Overclocking avanzado.
- Timings de RAM.
- Subtensiones.
- Bifurcación PCIe.
- Resizable BAR.
- RAID avanzado.
- ECC Registered.
- Diseño eléctrico de VRM.
- Cálculos térmicos avanzados.

---

# 42. Posible estructura para impartirla

## 5 min — Problema inicial

Mostrar:

- una placa;
- dos CPU;
- dos módulos RAM;
- dos discos.

Preguntar:

> ¿Cuál de estas piezas podemos montar juntas?

---

## 10 min — Explicación

Trabajar:

- CPU + socket + chipset + BIOS;
- RAM;
- SATA/M.2;
- PCIe;
- fuente.

---

## 10–15 min — Comprobación real

Elegir una placa del aula.

Buscar:

- ficha técnica;
- CPU Support List;
- RAM soportada;
- almacenamiento;
- expansión.

---

## 20–30 min — Trabajo por grupos

Cada grupo estudia su propio conjunto de componentes.

---

# 43. Idea final

La competencia que buscamos no es:

> **Memorizar qué CPU sirve para cada placa.**

La competencia es:

> **Ser capaz de identificar un componente, localizar documentación técnica fiable y justificar si es compatible con otro componente.**
