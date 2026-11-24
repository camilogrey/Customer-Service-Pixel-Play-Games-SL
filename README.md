# Customer-Service-Pixel-Play-Games-SL
OBJETIVO GENERAL: Dar solución a las diferentes necesidades o problemas de PixelPlay mediante una solución personalizada de servicio al cliente (PixelPlay Service), empaquetada como solución no administrada.

# Práctica D365 Customer Service — PixelPlay Games

**Nov 12, 2026 @Jose Antonio**

---

## Objetivos de la práctica

El alumno implantará Dynamics 365 Customer Service para el servicio de atención al cliente de una cadena de videojuegos, desde la configuración estándar hasta la personalización de sus procesos de negocio. Al terminar debe saber justificar cada decisión funcional, no solo configurarla.

| Área | Conceptos de Dynamics 365 Customer Service que se trabajan |
| --- | --- |
| **Modelo de servicio** | Cuentas, contactos, casos, temas (árbol de *subjects*), productos, prioridad, origen, estado y razón para el estado |
| **Gestión de casos** | Casos primarios y secundarios, combinar casos, actividades (correo, llamada, tarea), escala de tiempos, resolución y cancelación, reapertura, escalado de casos |
| **Organización del trabajo** | Colas públicas y privadas, elementos de cola, equipos y unidades de negocio |
| **Acuerdos de servicio** | Derechos (*entitlements*), canales del derecho, SLA mejorados con KPI de primera respuesta y resolución, acciones de aviso e incumplimiento, calendario de servicio y festivos, pausa del SLA |
| **Conocimiento** | Artículos de conocimiento, ciclo de aprobación y publicación, búsqueda desde el caso, vincular artículo al caso |
| **Entrada de casos** | Reglas de creación y actualización automática de registros (correo a caso), plantillas de correo y firmas |
| **Omnicanal y enrutamiento** | Enrutamiento unificado, flujos de trabajo, reglas de clasificación y asignación, habilidades, capacidad, presencia, chat en vivo |
| **Personalización** | Tablas personalizadas, columnas, relaciones, formularios, vistas, columnas calculadas y de resumen, soluciones y editor |
| **Procesos de negocio** | Flujos de proceso de negocio (BPF) con etapas, pasos obligatorios y ramificación, reglas de negocio, flujos de Power Automate |
| **Seguridad** | Roles de seguridad, privilegios por tabla, perfiles de seguridad de columna |
| **Medición** | Paneles, vistas personales y del sistema, *Customer Service historical analytics*, encuestas de Customer Voice |

**Duración orientativa:** 30-40 horas, en grupos de 2-3 alumnos, sobre un entorno de prueba con Customer Service y una solución propia llamada **PixelPlay Service** (prefijo de editor `ppg`).

---

## Escenario: PixelPlay Games, S.L.

PixelPlay Games es una cadena española que vende videojuegos, consolas y accesorios a través de su tienda online y de 14 tiendas físicas. Factura 48 M€ al año, tiene 210.000 clientes registrados y su servicio de atención al cliente lo forman 38 personas en Madrid y Valencia.

### Líneas de negocio que generan consultas al servicio

* **Venta online y en tienda:** juegos físicos, consolas, periféricos y merchandising. Envíos peninsulares en 24-48 h, Baleares y Canarias en 3-5 días.
* **Productos digitales:** códigos de descarga, tarjetas prepago y suscripciones que se envían por correo al comprar.
* **Reservas (preventas):** el cliente paga una señal de 10 € y recibe el juego el día de lanzamiento, con un regalo exclusivo de reserva.
* **Programa Retro y recompra:** el cliente entrega juegos o consolas usados a cambio de saldo en tienda; PixelPlay los revende como seminuevos con 1 año de garantía.
* **Servicio técnico:** reparación de consolas y mandos, propia o derivada al fabricante cuando el producto está en garantía de marca.
* **Club PixelPoints:** programa de fidelización con tres niveles (Bronce, Plata y Leyenda) según el gasto anual.
* **Ventas a empresas:** salones de juego, cibercafés y centros educativos que compran en volumen con un contrato de soporte.

### Organización del servicio de atención al cliente

| Equipo | Atiende | Personas |
| --- | --- | --- |
| **Primer nivel (Front)** | Consultas generales, pedidos, envíos, reservas y PixelPoints | 22 |
| **Pedidos y devoluciones** | Devoluciones, reembolsos, incidencias con transportistas | 6 |
| **Soporte técnico** | Averías, garantías, reparaciones y códigos digitales que no funcionan | 6 |
| **Cuentas empresa** | Clientes con contrato B2B | 2 |
| **Supervisión** | Escalados, reclamaciones formales y Hojas de Reclamaciones de consumo | 2 |

**Horario de atención:** lunes a sábado de 9:00 a 21:00; los días de lanzamiento importante se amplía hasta las 23:00.  
**Canales actuales:** teléfono, dos buzones de correo (`atencion@` y `tecnico@`), chat de la web, WhatsApp y mensajes en redes sociales.

---

## Problemática actual

El último lanzamiento importante (la reserva de una consola nueva en octubre) colapsó el servicio: 9.400 contactos en 72 horas, un tiempo medio de primera respuesta de 3,5 días y la nota de satisfacción cayó de 7,8 a 4,9. La dirección ha decidido implantar Dynamics 365 Customer Service y os encarga el proyecto.

En las entrevistas con el equipo se han detectado estos problemas:

1. **Sin registro único:** cada canal se gestiona en su herramienta (centralita, Outlook, WhatsApp Web). Un mismo cliente escribe por tres vías y lo atienden tres agentes distintos que no saben nada unos de otros.
2. **Sin clasificación:** no hay una tipología de consultas, así que no se sabe cuánto pesan los problemas de envío frente a los de códigos digitales o garantías.
3. **Reparto manual:** un coordinador lee los buzones cada mañana y reenvía correos a mano. Lo técnico llega al Front y lo comercial al técnico.
4. **Sin compromisos de tiempo:** no existe un plazo de respuesta pactado. Los clientes Leyenda y las empresas con contrato esperan lo mismo que cualquiera, y los contratos B2B prometen respuesta en 4 horas laborables que nadie mide.
5. **Picos de lanzamiento:** cuando sale un juego esperado, cientos de clientes preguntan lo mismo («no me ha llegado la reserva»). Cada consulta se trata por separado aunque la causa sea una sola incidencia del transportista.
6. **Códigos digitales:** el 18 % de los contactos son códigos que «no funcionan». Unos son errores del cliente (región equivocada, plataforma distinta) y otros son códigos defectuosos que hay que reponer. Se resuelve de memoria y cada agente lo hace a su manera.
7. **Devoluciones y garantías sin proceso:** no hay pasos definidos para decidir si procede devolución en 14 días, reparación propia, envío al fabricante o garantía Retro. Se pierden productos entre tienda, almacén y servicio técnico, y no se sabe en qué punto está cada uno.
8. **El conocimiento está en las personas:** las respuestas sobre compatibilidades, regiones, condiciones de reserva o garantías están en un Excel compartido y en la cabeza de los veteranos. Los refuerzos contratados para Navidad tardan semanas en ser autónomos.
9. **Reclamaciones formales sin control:** las Hojas de Reclamaciones de consumo tienen un plazo legal de respuesta y algunas se han contestado fuera de plazo.
10. **Datos de pago visibles para todos:** cualquier agente puede ver y modificar importes de reembolso.
11. **Sin medición:** la dirección no tiene datos de volumen por canal, tiempos, causas ni satisfacción; solo quejas en redes sociales.

**Encargo:** diseñar e implantar en Dynamics 365 Customer Service una solución que resuelva estos 11 problemas, preparada para la campaña de Navidad y el próximo gran lanzamiento.

---

## Requisitos y tareas

La práctica se divide en 10 bloques. Cada bloque indica el problema que resuelve; el grupo debe documentar qué configuró y por qué.

### Bloque 1 - Estructura organizativa y seguridad (problemas 3 y 10)
1. Crear la unidad de negocio raíz `PixelPlay` y dos subunidades: `Madrid` y `Valencia`.
2. Crear los equipos `Front`, `Pedidos y devoluciones`, `Soporte técnico`, `Cuentas empresa` y `Supervisión`.
3. Crear un rol personalizado «Agente PixelPlay» copiando el rol estándar de representante del servicio de atención al cliente, con lectura de casos de toda la organización y escritura solo en los de su unidad.
4. Crear un perfil de seguridad de columna que oculte el importe de reembolso a todos salvo a `Pedidos y devoluciones` y `Supervisión`.
5. Crear al menos un usuario o equipo de prueba por perfil y demostrar qué ve cada uno.

### Bloque 2 - Datos maestros (problema 1)
1. Cargar con la herramienta de importación las cuentas, contactos y productos de la sección **Datos de partida**.
2. Crear los productos en el catálogo con su familia (*Consolas*, *Juegos físicos*, *Juegos digitales*, *Accesorios*, *Seminuevos Retro*).
3. Añadir al contacto la columna `Nivel PixelPoints` (opción: *Bronce*, *Plata*, *Leyenda*) y la columna `Saldo PixelPoints`.

### Bloque 3 - Casos y clasificación (problemas 1 y 2)
1. Diseñar el árbol de temas con al menos tres niveles. Ejemplo de rama: `Pedidos › Envío › Retraso del transportista`.
2. Ramas mínimas: `Pedidos`, `Reservas`, `Productos digitales`, `Devoluciones y garantías`, `Servicio técnico`, `Programa Retro`, `PixelPoints`, `Reclamación formal`.
3. Añadir al caso los orígenes *WhatsApp* y *Redes sociales* y las razones para el estado «Esperando al cliente», «Esperando al fabricante» y «Esperando al almacén».
4. Registrar 5 casos de ejemplo por canales distintos, con actividades de llamada y correo en la escala de tiempo.
5. Demostrar la combinación de dos casos duplicados del mismo cliente y la resolución de un caso con tiempo facturable.

### Bloque 4 - Incidencias masivas en lanzamientos (problema 5)
1. Simular el retraso del transportista en el lanzamiento: crear un caso primario «Incidencia transporte lanzamiento» y 6 casos secundarios.
2. Configurar la herencia de columnas de primario a secundario y la regla de cierre en cascada.
3. Demostrar que al resolver el caso primario se resuelven los secundarios y se avisa a cada cliente con una plantilla de correo.

### Bloque 5 - Colas y entrada automática de casos (problemas 1 y 3)
1. Crear las colas `Front`, `Pedidos y devoluciones`, `Soporte técnico`, `Cuentas empresa` y `Reclamaciones`.
2. Configurar una regla de creación y actualización automática de registros para cada buzón: los correos de clientes conocidos generan caso; las respuestas a un caso abierto se añaden a ese caso en lugar de crear uno nuevo.
3. Crear plantillas de correo de acuse de recibo, solicitud de información y cierre, y una firma corporativa.

### Bloque 6 - Derechos, SLA y calendarios (problemas 4 y 9)
1. Crear el calendario de servicio PixelPlay (L-S 9-21 h) con los festivos nacionales de 2026 y 2027.
2. Crear los derechos: *Estándar*, *Leyenda* (prioridad alta) y *Contrato empresa* (40 casos al año, canales teléfono y correo).
3. Crear un SLA mejorado con estos KPI:

| Tipo de cliente o caso | Primera respuesta | Resolución | Aviso previo |
| --- | --- | --- | --- |
| **Estándar** | 24 h laborables | 5 días laborables | 75% del plazo |
| **Leyenda** | 8 h laborables | 3 días laborables | 75% del plazo |
| **Contrato empresa** | 4 h laborables | 2 días laborables | 50% del plazo |
| **Reclamación formal** | 48 h | 30 días naturales | 20 días naturales |

4. El SLA se pausa cuando la razón para el estado es «Esperando al cliente».
5. Acciones: correo al supervisor al llegar al aviso y reasignación a la cola `Supervisión` al incumplirse.
6. Mostrar el temporizador del SLA en el formulario de caso.

### Bloque 7 - Base de conocimiento (problemas 6 y 8)
1. Redactar y publicar 6 artículos: *compatibilidad de regiones*, *canje de códigos por plataforma*, *condiciones de reserva*, *plazos de devolución*, *garantía Retro* y *canje de PixelPoints*.
2. Aplicar el ciclo borrador $\rightarrow$ revisión $\rightarrow$ aprobado $\rightarrow$ publicado, con un revisor del equipo `Supervisión`.
3. Configurar la búsqueda de conocimiento en el formulario de caso filtrada por el tema del caso.
4. Resolver un caso de código digital vinculando y enviando un artículo al cliente.

### Bloque 8 - Personalización del modelo de datos (problemas 6 y 7)
1. Crear la tabla **Solicitud RMA** (`ppg_solicitudrma`) relacionada N:1 con Caso, Contacto y Producto.
2. Columnas mínimas: número de serie, fecha de compra, canal de compra, tipo (*Devolución*, *Garantía propia*, *Garantía de fabricante*, *Garantía Retro*), estado físico, diagnóstico, importe de reembolso, número de seguimiento.
3. Columna calculada *Días desde la compra* y columna de resumen *Número de RMA del contacto*.
4. Crear la tabla **Código digital** (`ppg_codigodigital`) con código, plataforma, región, estado (*Activo*, *Canjeado*, *Defectuoso*, *Repuesto*) y código sustituto.
5. Diseñar formularios principal y rápido y dos vistas por tabla, y añadir ambas tablas como subcuadrícula en el formulario de caso.

### Bloque 9 - Procesos de negocio (problemas 6, 7 y 9)

#### 9.1 Flujo de proceso de negocio «Devolución y garantía» sobre Solicitud RMA, con ramificación:
1. **Recepción:** comprobar ticket de compra, número de serie y fecha. Paso obligatorio.
2. **Valoración:** rama según *Días desde la compra* y tipo.
   * *Hasta 14 días y producto sin usar* $\rightarrow$ etapa **Devolución:** aceptación, importe de reembolso, abono.
   * *Más de 14 días y dentro de garantía de marca* $\rightarrow$ etapa **Envío a fabricante:** número de seguimiento y fecha de respuesta del fabricante.
   * *Producto seminuevo Retro* $\rightarrow$ etapa **Reparación propia:** diagnóstico, coste y decisión reparar o sustituir.
3. **Cierre:** comunicación al cliente y encuesta. Al terminar el proceso se resuelve el caso.

#### 9.2 Flujo de proceso de negocio «Reclamación formal» sobre Caso
Registro, análisis, propuesta de respuesta, aprobación del supervisor y respuesta. Debe convivir con el proceso estándar de caso y activarse solo para el tema *Reclamación formal*.

#### 9.3 Reglas de negocio
* Si el tipo de RMA es *Devolución*, el importe de reembolso es obligatorio; en el resto se oculta.
* Si el tema es *Productos digitales*, la subcuadrícula *Código digital* es visible y la plataforma obligatoria.
* Si el contacto es nivel *Leyenda*, la prioridad del caso pasa a *Alta*.

#### 9.4 Flujos de Power Automate
* Cuando un código digital se marca *Defectuoso*, asignar un código sustituto libre de la misma plataforma y región, y enviarlo al cliente por correo.
* Cuando una Solicitud RMA lleva 10 días en la etapa *Envío a fabricante*, crear una tarea de seguimiento para el agente.
* Cuando se resuelve un caso de cliente *Plata* o *Leyenda*, sumar 50 PixelPoints como compensación si hubo incumplimiento de SLA.

### Bloque 10 - Omnicanal, enrutamiento y medición (problemas 1, 3, 5 y 11)
1. Configurar el enrutamiento unificado de casos con reglas de clasificación por tema y nivel del cliente, y reglas de asignación por habilidad (*Consolas*, *Digital*, *B2B*) y capacidad.
2. Configurar el canal de chat en la web con un formulario previo que pida correo y número de pedido, y definir estados de presencia.
3. Crear una encuesta de Customer Voice que se envíe al resolver el caso.
4. Crear un panel para `Supervisión` con: casos abiertos por cola, casos por tema, SLA incumplidos, volumen por canal y satisfacción media.
5. *Opcional:* activar Copilot en el espacio de trabajo y comparar el resumen de un caso con el escrito por el agente.

---

## Datos de partida

Todos los datos son ficticios. El grupo puede ampliarlos, pero debe cargar como mínimo estos registros para las pruebas.

### Cuentas (clientes empresa)

| Cuenta | Tipo | Derecho | Ciudad |
| --- | --- | --- | --- |
| **Arena Gaming Center S.L.** | Salón de juego | Contrato empresa | Madrid |
| **CiberNexus Valencia** | Cibercafé | Contrato empresa | Valencia |
| **Colegio Tecnológico Sierra Norte** | Centro educativo | Estándar | Alcobendas |

### Contactos

| Contacto | Nivel PixelPoints | Cuenta | Situación para las pruebas |
| --- | --- | --- | --- |
| **Lucía Ferrer** | Leyenda | *(Sin asignar)* | Reserva de la consola nueva no recibida |
| **Marcos Ibáñez** | Bronce | *(Sin asignar)* | Código digital de región equivocada |
| **Ana Beltrán** | Plata | *(Sin asignar)* | Mando con deriva del joystick a los 8 meses |
| **Diego Salas** | Bronce | *(Sin asignar)* | Quiere devolver un juego a los 10 días |
| **Paula Roig** | Leyenda | *(Sin asignar)* | Consola Retro seminueva que no lee discos |
| **Javier Moreno** | *(Sin nivel)* | Arena Gaming Center S.L. | 6 consolas del salón sin conexión online |
| **Elena Camps** | *(Sin nivel)* | CiberNexus Valencia | Factura de pedido B2B duplicada |
| **Raúl Ortega** | Plata | *(Sin asignar)* | Presenta una Hoja de Reclamaciones por retraso |

### Productos

| Producto | Familia | Garantía |
| --- | --- | --- |
| **Consola NovaStation 6** | Consolas | 3 años de fabricante |
| **Mando inalámbrico NovaPad** | Accesorios | 3 años de fabricante |
| **Juego «Crónicas de Ébano» (físico)** | Juegos físicos | 3 años legal |
| **Código «Crónicas de Ébano» (digital)** | Juegos digitales | Sin devolución tras canje |
| **Consola Retro NovaStation 4 reacondicionada** | Seminuevos Retro | 1 año PixelPlay |
| **Tarjeta prepago 50 €** | Juegos digitales | Sin devolución tras canje |

**Códigos digitales para el flujo de sustitución:** 10 códigos de la plataforma *NovaStation* región Europa en estado *Activo*, 2 de región América y 1 marcado como *Defectuoso*.

---

## Entregables y evaluación

Cada grupo entrega la solución exportada, una memoria y una demostración en vivo de 20 minutos.

* **Solución PixelPlay Service exportada como no administrada**, con todas las personalizaciones dentro (nada en la solución predeterminada).
* **Presentación en PPT** para exponer y defender la decisión de diseño de cada bloque, capturas de la configuración y qué problema del 1 al 11 resuelve.
* **Mapa de temas** y diagrama del flujo de proceso «Devolución y garantía» con sus ramas.
* **Demostración en vivo** de los tres casos de prueba obligatorios.
* **Respuesta razonada** a la pregunta de reflexión.

### Casos de prueba obligatorios en la demostración

1. **Lucía Ferrer (Leyenda)** escribe al buzón `atencion@` porque no le ha llegado la reserva: el caso se crea solo, entra con prioridad alta, se vincula al caso primario de la incidencia de transporte y muestra su SLA de 8 h.
2. **Marcos Ibáñez** abre un chat por un código que no funciona: el agente encuentra el artículo de regiones, detecta que el código es defectuoso, lo marca y el cliente recibe el sustituto de forma automática.
3. **Ana Beltrán** entrega su mando en tienda: se abre la Solicitud RMA, el flujo de proceso toma la rama *Envío a fabricante* y, al cerrarse, se envía la encuesta.

### Criterios de evaluación

| Criterio | Peso |
| --- | --- |
| **Modelo de servicio, casos, temas y colas (bloques 2-5)** | 20% |
| **Derechos, SLA y calendarios (bloque 6)** | 15% |
| **Base de conocimiento (bloque 7)** | 10% |
| **Personalización del modelo de datos (bloque 8)** | 15% |
| **Procesos de negocio: BPF, reglas y flujos (bloque 9)** | 20% |
| **Seguridad, omnicanal y medición (bloques 1 y 10)** | 10% |
| **Memoria y demostración: justificación de decisiones** | 10% |

---

> **Pregunta de reflexión:** La dirección quiere que, en el próximo lanzamiento, los clientes **Leyenda** sean atendidos siempre antes que nadie. Explicad qué combinación de derechos, SLA, reglas de negocio y enrutamiento usaríais, qué riesgo tiene para el resto de clientes y cómo lo mediríais en el panel.
