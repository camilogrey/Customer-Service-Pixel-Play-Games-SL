# Semana 1: Configuración Base, Estructura y Datos Maestros

## Día 1 (Trabajo Conjunto)
- **Todos:** Creación y configuración inicial de la solución no administrada PixelPlay Service con prefijo `ppg_`.

## Días 2–3 (Trabajo Conjunto)
- **Todos:** Implementación del Bloque 1 (Unidad de negocio raíz PixelPlay, subunidades Madrid y Valencia, creación de equipos Front, Pedidos y devoluciones, Soporte técnico, Cuentas empresa y Supervisión, y rol personalizado "Agente PixelPlay").

## Días 4–5
- **Todos:** Ejecución del Bloque 2 (Carga de datos maestros de cuentas, contactos y productos con la herramienta de importación, creación de familias de productos, y adición de las columnas de nivel y saldo de PixelPoints).

---

# Semana 2: Desarrollo Paralelo por Módulos Independientes

## Días 6–8
- **Miembro 1 (Modelo de Datos):** Bloque 8 (Parte 1): Creación de la tabla personalizada `ppg_solicitudrma` (relaciones N:1 con Caso, Contacto y Producto, y columnas mínimas).
- **Miembro 2 (Gestión de Casos y Colas):**
  - Bloque 3: Diseño del árbol de temas (mínimo tres niveles y ramas requeridas), adición de orígenes WhatsApp y Redes sociales, y razones para el estado.
  - Bloque 5 (Parte 1): Creación de las colas públicas y privadas para cada equipo.
- **Miembro 3 (Base de Conocimiento y Canales):** Bloque 7 (Parte 1): Redacción de los 6 artículos de conocimiento y configuración del ciclo de aprobación con revisor del equipo Supervisión.

## Días 9–10
- **Miembro 1 (Modelo de Datos):** Bloque 8 (Parte 2): Creación de la tabla `ppg_codigodigital`, columnas calculadas de Días desde la compra, columnas de resumen, formularios y subcuadrículas en el caso.
- **Miembro 2 (SLA y Derechos):** Bloque 6: Creación del calendario de servicio (L-S 9-21h) con festivos de 2026-2027, derechos (Estándar, Leyenda, Contrato empresa) y SLA mejorados con KPI, avisos y pausas.
- **Miembro 3 (Base de Conocimiento y Canales):** Bloque 7 (Parte 2) y Bloque 10 (Parte 2): Configuración de la búsqueda de conocimiento filtrada por tema en el formulario de caso. Configuración inicial del canal de chat web, formulario previo y estados de presencia.

---

# Semana 3: Automatización Avanzada, Procesos y Enrutamiento

## Días 11–13
- **Miembro 1 (Automatización y Reglas):**
  - Bloque 9 (Parte 1): Implementación de las Reglas de negocio (obligatoriedad de importe en RMA, visibilidad de códigos digitales, prioridad Alta para nivel Leyenda).
  - Bloque 9 (Parte 2): Creación de los 3 flujos de Power Automate (sustitución automática de códigos digitales defectuosos, tarea de seguimiento RMA a los 10 días, y compensación de PixelPoints por incumplimiento de SLA).
- **Miembro 2 (Procesos de Negocio y Casos Masivos):**
  - Bloque 4: Simulación de incidencias masivas en lanzamientos (caso primario de transporte y 6 secundarios con herencia y cierre en cascada).
  - Bloque 9 (Parte 3): Desarrollo del Flujo de Proceso de Negocio (BPF) de "Devolución y garantía" con sus ramificaciones, y el BPF de "Reclamación formal".
- **Miembro 3 (Omnicanal y Analítica):**
  - Bloque 5 (Parte 2): Configuración de las reglas de creación y actualización automática de registros (correo a caso) y plantillas de correo/firma corporativa.
  - Bloque 10 (Parte 1): Configuración del enrutamiento unificado de casos (reglas de clasificación por tema/nivel y reglas de asignación por habilidades y capacidad).

## Días 14–15
- **Miembro 1:** Soporte en depuración de reglas de negocio y flujos de Power Automate.
- **Miembro 2:** Ajustes finales en los BPFs de RMA y validación de herencia de casos secundarios.
- **Miembro 3:** Bloque 10 (Parte 3): Creación de la encuesta de Customer Voice y diseño del panel de supervisión (casos abiertos, por tema, SLA incumplidos, volumen por canal y satisfacción).

---

# Semana 4: Pruebas Integrales, Documentación y Defensa

## Días 16–17 (Trabajo Conjunto)
- **Todos:** Pruebas de integración del sistema completo.
- **Todos:** Ejecución y validación de los 3 casos de prueba obligatorios (Lucía Ferrer, Marcos Ibáñez y Ana Beltrán) para comprobar que flujos, SLA, colas y automatizaciones conectan correctamente.

## Días 18–19 (Trabajo Conjunto)
- **Todos:** Resolución documentada y debate técnico de la pregunta de reflexión sobre la priorización de clientes Leyenda.
- **Todos:** Exportación final de la solución no administrada PixelPlay Service.
- **Miembros 1 y 2:** Redacción de la memoria técnica y justificación de decisiones funcionales por bloque.
- **Miembro 3:** Diseño de la presentación en PowerPoint para exponer los 11 problemas resueltos y capturas de configuración.

## Día 20 (Trabajo Conjunto)
- **Todos:** Ensayo general de la demostración en vivo de 20 minutos, revisión final de entregables y empaquetado de la solución.