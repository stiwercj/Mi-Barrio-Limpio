# Mi Barrio Limpio, Mi Comunidad Unida — Prototipo Funcional (TRL 5)

Prototipo funcional de aplicación móvil con gamificación vecinal desarrollado bajo enfoque **No-Code** (**Google AppSheet** + **Google Sheets**) y metodología ágil (**AEGIS-MD / RAD**) para el reporte colaborativo de puntos críticos de residuos sólidos en la cabecera urbana de **Granada, Meta**.

> **Alcance académico:** Este desarrollo corresponde a un prototipo funcional de nivel de maduración tecnológica **TRL 5** (validado en entorno simulado/comunitario) para el curso **Proyecto de Grado (202016907)** de la **UNAD**[cite: 1, 9]. No sustituye el servicio público de aseo ni radica solicitudes oficiales ante la administración municipal[cite: 9].

---

## Equipo de Desarrollo y Tutoría
* **Autores:** Lowren Orlando Traslaviña Santos, Stiwer Andrés Castillo Jiménez, Yesica Eylin Rojas Monsalve[cite: 9]
* **Tutor:** Wilson Hernán Pérez Correa[cite: 9]
* **Programa:** Ingeniería de Sistemas — ECBTI (UNAD)[cite: 9]

---

## Arquitectura No-Code y Diccionario de Datos
Al emplear la plataforma *No-Code* **Google AppSheet**, la lógica del sistema se implementa mediante modelos de datos relacionales, expresiones declarativas y vistas configurables[cite: 9]:

* **Fuente de datos:** Tabla `Basededatos_ProyectoG` (Google Sheets)[cite: 9].
* **Estructura y reglas configuradas:**
  * `ID_Reporte`: Valor inicial `UNIQUEID()`, edición bloqueada (`Editable = OFF`) y visibilidad restringida únicamente a la vista de detalle mediante `CONTEXT("ViewType") = "Detail"`[cite: 9].
  * `Fecha`: Valor inicial automático `TODAY()`[cite: 9].
  * `Barrio`: Configurada como etiqueta principal (`Label`) y campo obligatorio (`Required = ON`)[cite: 9].
  * `Descripción`: Campo obligatorio para describir el punto crítico reportado[cite: 9].
  * `Foto`: Evidencia fotográfica obligatoria del foco de residuos[cite: 9].
  * `Ubicacion_LatLong`: Captura automática de coordenadas GPS mediante `HERE()` y marcada como obligatoria[cite: 9].
  * `Puntos_Otorgados`: Valor inicial `10` con edición deshabilitada (`Editable = OFF`) para evitar la duplicación de puntaje al modificar reportes existentes[cite: 9].

---

## Lógica de Gamificación y Ranking por Barrio
* **Vista Clasificación (Ranking):** Agrupada por `Barrio` utilizando la función de agregado `SUMA :: Puntos_Otorgados`, lo que permite visualizar el puntaje acumulado por sector sin exponer identificadores técnicos en los encabezados[cite: 9].
* **Regla de incentivo:** Basada en el reconocimiento social y el orgullo vecinal (sin recompensas económicas), incentivando la sana competencia entre barrios[cite: 9].

---

## Matriz de Pruebas y Validación TRL 5
1. **Registro completo y sincronización:** Verificación de captura de `Barrio`, `Descripción`, `Foto` y `HERE()`, asignando `10` puntos y sincronizando en Google Sheets[cite: 9].
2. **Acumulación por barrio en Ranking:** Verificación de suma agrupada por sector (`centro` = 20 pts vs. `porvenir` = 10 pts)[cite: 9].
3. **Integridad del puntaje en edición:** Comprobación de que editar la descripción de un reporte existente mantiene intacto `Puntos_Otorgados`[cite: 9].
4. **Validación de campos obligatorios:** Bloqueo de guardado cuando faltan campos requeridos (`This entry is required`)[cite: 9].
5. **Validación simulada con participantes (n = 20) y líderes (n = 2):** Evaluación estructurada (escala Likert + escala de usabilidad SUS promedio de `90.25 / 100`, superando la meta interna $\ge 75$) en los barrios Centro, Antonio Ricaurte y Belén[cite: 11].

---

## Evidencias y Enlaces del Proyecto
* **Prototipo funcional en Google AppSheet:** `[Pega aquí el enlace de tu app en AppSheet]`[cite: 9]
* **Video demostrativo (máx. 10 min):** `[Pega aquí el enlace de YouTube o Drive]`[cite: 9]
* **Instrumentos y validación simulada:** Ver archivo `Encuestas_y_Entrevistas_Simuladas_Mi_Barrio_Limpio_TRL5.docx` adjunto en este repositorio[cite: 11].
