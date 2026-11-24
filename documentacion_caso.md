# Documentación del Taller: Configuración de Dynamics 365 / Power Platform

Este documento registra los pasos de configuración realizados en el entorno de **Dynamics 365 / Power Platform** para la organización **PixelPlay Games SL**.

---

## Bloque 1: Estructura Organizativa y Seguridad

### 1. Configuración de Unidades de Negocio (*Business Units*)

Se estructuró la jerarquía organizativa de la empresa creando las unidades de negocio correspondientes a la sede central y delegaciones locales.

* **Estructura creada:**
  * **PixelPlay** (Unidad principal bajo el entorno raíz `3618-pixelplaygamessl-gamesofcod`).
  * **Madrid** (Unidad de negocio dependiente de `PixelPlay`).
  * **Valencia** (Unidad de negocio dependiente de `PixelPlay`).

![Unidades de negocio](img/)

---

### 2. Creación de Equipos (*Teams*)

Se crearon los equipos de trabajo propietarios y de acceso para gestionar la asignación de registros y la colaboración entre áreas dentro de las distintas unidades de negocio.

* **Equipos creados:**
  * `Front` (Asignado a la unidad de negocio *PixelPlay*).
  * `Madrid` (Asignado a la unidad de negocio *Madrid*).
  * `Pedidos y devoluciones` (Asignado a la unidad de negocio *PixelPlay*).
  * `PixelPlay` (Asignado a la unidad de negocio *PixelPlay*).
  * `Soporte técnico` (Asignado a la unidad de negocio *PixelPlay*).
  * `Supervisión` (Asignado a la unidad de negocio *PixelPlay*).

![Creación de Equipos](2.%20Creacion%20de%20Equipos.png)

---

### 3. Creación y Configuración del Rol de Seguridad `Agente PixelPlay`

#### Paso 3.1: Selección del Rol Base
Para establecer los permisos iniciales, se tomó como base el rol predeterminado de Dynamics 365 **Customer Service Representative**.

![Selección de rol base](3.%20Creacion%20Pixelplay%20rol%20a%20partir%20CS%20Representative.png)

#### Paso 3.2: Copia del Rol de Seguridad
Se realizó una copia del rol seleccionado asignándole el nombre **Agente PixelPlay**.

![Copia del rol Agente PixelPlay](3.1.%20CReacion%20del%20Pixel%20Play%20.png)

#### Paso 3.3: Verificación de la Creación del Rol
Se comprobó que el nuevo rol no administrado **Agente PixelPlay** figura correctamente guardado dentro del listado de *Security roles* del entorno.

![Rol final creado](3.2%20creado%20el%20rol%20final.png)

#### Paso 3.4: Ajuste de Privilegios en la Tabla Caso (*Case*)
Se modificaron los privilegios del rol **Agente PixelPlay** para la entidad de Servicio `Case` (*Caso / Incidencia*):
* **Lectura (*Read*):** Configurado a nivel **Organización** (*Organization*), permitiendo al agente leer casos de toda la empresa.
* **Escritura (*Write*):** Configurado a nivel **Unidad de Negocio** (*Business Unit*), restringiendo la modificación de casos únicamente a los de su propia unidad.

![Configuración de privilegios de Lectura y Escritura](3.3%20Permissos%20de%20lectura%20de%20casos%20universales%20y%20escritura%20de%20unidad%20de%20negocio.png)

#### Paso 3.5: Confirmación de Configuración del Rol
Se guardaron y publicaron las modificaciones del rol de seguridad, dejando establecidos los privilegios requeridos para los agentes.

![Rol de seguridad finalizado](3.4%20rol%20de%20seguridad%20pixelplay%20finalizado%20.png)

---

## Bloque 2: Personalización y Soluciones

### 4. Creación de la Solución `PixelPlay Service`

Se creó la solución contenedor en Power Apps para empaquetar todas las personalizaciones y componentes de la práctica.

* **Propiedades de la solución:**
  * **Display name:** `PixelPlay Service`
  * **Name:** `PixelPlayService`
  * **Publisher:** `pixelplaysolution (pixelplaysolution)`
  * **Version:** `1.0.0.0`

![Creación de solución](4.%20Creacion%20de%20solucion.png)

---

### 5. Personalización de la Tabla Contactos (*Contacts*)

#### Paso 5.1: Creación de la Columna `Nivel PixelPoints`
Dentro de la tabla **Contacts**, se creó la columna de tipo **Choice** (Opción) denominada **Nivel PixelPoints** para categorizar el nivel de fidelidad de los contactos con los siguientes valores:
1. **Bronce** (Valor: `894.310.000`)
2. **Plata** (Valor: `894.310.001`)
3. **Leyenda** (Valor: `894.310.002`)

![Columna Nivel PixelPoints en Contactos](5.1.%20Tabla%20Contacto%20Columna%20Nivel%20PixelPoints.png)

---

## Resumen del Estado Actual

Hasta este punto se han completado con éxito:
1. La estructura jerárquica de **Unidades de Negocio** y **Equipos**.
2. El rol de seguridad **Agente PixelPlay** con sus privilegios sobre Casos.
3. La solución no administrada **PixelPlay Service**.
4. La adición del campo **Nivel PixelPoints** a la entidad **Contact**.