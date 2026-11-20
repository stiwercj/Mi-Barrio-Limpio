# Mi Barrio Limpio, Mi Comunidad Unida — Prototipo Funcional (TRL 5)

Prototipo funcional de aplicación móvil con gamificación vecinal desarrollado bajo enfoque **No-Code** (**Google AppSheet** + **Google Sheets**) y metodología ágil (**AEGIS-MD / RAD**) para el reporte colaborativo de puntos críticos de residuos sólidos en la cabecera urbana de **Granada, Meta**.

> **Alcance académico:** Este desarrollo corresponde a un prototipo funcional de nivel de maduración tecnológica **TRL 5** (validado en entorno simulado/comunitario) para el curso **Proyecto de Grado (202016907)** de la **UNAD**. No sustituye el servicio público de aseo ni radica solicitudes oficiales ante la administración municipal.

> **Nota sobre la arquitectura No-Code y ausencia de código fuente tradicional:** De acuerdo con el Marco Tecnológico del proyecto, el prototipo funcional fue desarrollado mediante la plataforma **No-Code Google AppSheet** conectada a un backend relacional en **Google Sheets** bajo enfoque ágil **RAD / AEGIS-MD**. En este paradigma de ingeniería de software, la lógica de negocio, la interfaz móvil, las validaciones de entrada y la captura de sensores (GPS y cámara) no se construyen mediante código fuente compilado o archivos de programación tradicional, sino a través de modelos tabulares, expresiones declarativas (`UNIQUEID()`, `TODAY()`, `HERE()`, `CONTEXT()`), reglas de integridad de datos y vistas configurables alojadas en la nube de Google. Por ello, este repositorio centraliza la arquitectura de datos, la documentación técnica de reglas y fórmulas, la matriz de trazabilidad, los instrumentos de validación y las evidencias funcionales del prototipo.

---

## Equipo de Desarrollo y Tutoría
* **Autores:** Lowren Orlando Traslaviña Santos, Stiwer Andrés Castillo Jiménez, Yesica Eylin Rojas Monsalve
* **Tutor:** Wilson Hernán Pérez Correa
* **Programa:** Ingeniería de Sistemas — ECBTI (UNAD)

---

## Arquitectura No-Code y Diccionario de Datos
La lógica del sistema se implementa mediante modelos de datos relacionales, expresiones declarativas y vistas configurables:

* **Fuente de datos:** Tabla `Basededatos_ProyectoG` (Google Sheets).
* **Estructura y reglas configuradas:**
  * `ID_Reporte`: Clave primaria (`Key`), valor inicial `UNIQUEID()`, edición bloqueada (`Editable = OFF`) y visibilidad restringida únicamente a la vista de detalle mediante `CONTEXT("ViewType") = "Detail"`.
  * `Fecha`: Valor inicial automático `TODAY()`.
  * `Barrio`: Configurada como etiqueta principal (`Label`) y campo obligatorio (`Required = ON`).
  * `Descripción`: Campo obligatorio para describir el punto crítico reportado.
  * `Foto`: Evidencia fotográfica obligatoria del foco de residuos.
  * `Ubicacion_LatLong`: Captura automática de coordenadas GPS mediante `HERE()` y marcada como obligatoria.
  * `Puntos_Otorgados`: Valor inicial `10` con edición deshabilitada (`Editable = OFF`) para evitar la duplicación de puntaje al modificar reportes existentes.

---

## Lógica de Gamificación y Ranking por Barrio
* **Vista Clasificación (Ranking):** Agrupada por `Barrio` utilizando la función de agregado `SUMA :: Puntos_Otorgados`, lo que permite visualizar el puntaje acumulado por sector sin exponer identificadores técnicos en los encabezados.
* **Regla de incentivo:** Basada en el reconocimiento social y el orgullo vecinal (sin recompensas económicas), incentivando la sana competencia entre barrios.

---

## Matriz de Pruebas y Validación TRL 5
1. **Registro completo y sincronización:** Verificación de captura de `Barrio`, `Descripción`, `Foto` y `HERE()`, asignando `10` puntos y sincronizando en Google Sheets.
2. **Acumulación por barrio en Ranking:** Verificación de suma agrupada por sector (`centro` = 20 pts vs. `porvenir` = 10 pts).
3. **Integridad del puntaje en edición:** Comprobación de que editar la descripción de un reporte existente mantiene intacto `Puntos_Otorgados`.
4. **Validación de campos obligatorios:** Bloqueo de guardado cuando faltan campos requeridos (`This entry is required`).
5. **Validación simulada con participantes (n = 20) y líderes (n = 2):** Evaluación estructurada (escala Likert + escala de usabilidad SUS promedio de `90.25 / 100`, superando la meta interna $\ge 75$) en los barrios Centro, Antonio Ricaurte y Belén.

---

## Evidencias y Enlaces del Proyecto
* **Prototipo funcional en Google AppSheet:** `[Pega aquí el enlace de tu app en AppSheet]`
* **Video demostrativo (máx. 10 min):** `[Pega aquí el enlace de YouTube o Drive]`
* **Instrumentos y validación simulada:** Ver archivo `Encuestas_y_Entrevistas_Simuladas_Mi_Barrio_Limpio_TRL5.docx` adjunto en este repositorio.
