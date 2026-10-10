# Capítulo I: Introducción

**Proyecto personal:** MISTHY. **Autor:** Christoper Steven Rivas Castillo — CODERT0PH. **Versión:** 0.1.0. **Fecha de corte:** 9 de octubre de 2026, Lima.

Este capítulo presenta la visión del producto y sus hipótesis iniciales. El enunciado de Aplicaciones Web proporcionado por el autor se utiliza como guía de estructura; no convierte el proyecto en una entrega universitaria. No se incluyen NRC, profesor, integrantes ficticios ni resultados de investigación de usuarios que todavía no existen.

## Contenido

- [1.1. Startup Profile](#startup)
  - [1.1.1. Descripción de la startup](#descripcion)
  - [1.1.2. Perfil del autor](#autor)
- [1.2. Solution Profile](#solucion)
  - [1.2.1. Antecedentes y problemática](#problematica)
  - [1.2.2. Lean UX Process](#lean)
    - [1.2.2.1. Problem Statement](#problem-statement)
    - [1.2.2.2. Assumptions](#assumptions)
    - [1.2.2.3. Hypothesis Statements](#hypotheses)
    - [1.2.2.4. Lean UX Canvas](#canvas)
- [1.3. Segmentos objetivo](#segmentos)
- [Referencias y evidencia pendiente](#referencias)

<a id="startup"></a>
## 1.1. Startup Profile

<a id="descripcion"></a>
### 1.1.1. Descripción de la startup

MISTHY es una iniciativa personal de tecnología para la seguridad ciudadana en Perú. Propone conectar a personas, redes de confianza y organizaciones de apoyo mediante reportes privados, alertas, conservación de información y seguimiento de actuaciones. Su propósito es reducir la desorientación que puede experimentar una persona ante un robo, una amenaza o una presunta extorsión, especialmente cuando pierde acceso a su teléfono o no conoce el estado de la ayuda solicitada.

La iniciativa parte de una preocupación expresa del fundador: la inseguridad no termina con el hecho delictivo. También comprende el temor a represalias, las dificultades para recibir atención, el desgaste de repetir un relato y la percepción de que la posibilidad de obtener justicia depende de recursos económicos o contactos. Esa preocupación orienta el diseño; no se presenta como una relación causal ya demostrada.

**Misión propuesta:** facilitar que las personas pidan apoyo, organicen la información de un incidente y conserven visibilidad sobre las gestiones realizadas, con privacidad y acceso comprensible.

**Visión propuesta:** desarrollar una infraestructura de coordinación ciudadana que pueda crecer desde un piloto local hacia otras ciudades de Perú y Latinoamérica, con colaboración institucional cuando existan acuerdos verificables.

**Principios:** protección de la persona; privacidad por defecto; trazabilidad de acciones; acceso sin discriminación económica a las funciones esenciales; estados honestos; rechazo a la exposición pública de víctimas o sospechosos y a las represalias.

La marca se inspira en el Misti. Se mantiene la dirección visual púrpura `#6D28D9`, azul `#2563EB` y azul noche `#0F172A`, con Manrope e Inter. El diseño detallado pertenece al capítulo IV y a Figma, trabajados por separado con Claude.

El modelo de negocio es una hipótesis freemium: funciones esenciales de apoyo para ciudadanos y herramientas de coordinación para organizaciones. Los precios previos de S/ 9.90–14.90 para una suscripción personal y S/ 150–350 para organizaciones vecinales son rangos exploratorios, no tarifas validadas ni evidencia de disposición de pago. La atención crítica no se priorizará por plan contratado. No existe una empresa constituida ni un convenio policial acreditado en los materiales revisados.

<a id="autor"></a>
### 1.1.2. Perfil del autor y organización del trabajo

**Christoper Steven Rivas Castillo (CODERT0PH)** es el único participante y responsable de MISTHY. Estudia Ingeniería de Software, cursa el séptimo ciclo en la UPC y reside en Lima. Sus áreas de trabajo declaradas abarcan desarrollo con JavaScript, Vue, Vite, C#, Java y Python; bases de datos relacionales y MongoDB; Git/GitHub; ciberseguridad y creación de contenido educativo.

En este proyecto asume las decisiones de producto, investigación, documentación, desarrollo y validación. Codex y Claude son herramientas de apoyo; no son integrantes humanos ni reemplazan entrevistas, revisión de especialistas o evidencia de uso. La elaboración asistida de un documento no demuestra que se haya ejecutado el software descrito.

La documentación se divide en ramas `feature-capitulo1`, `feature-capitulo2` y `feature-capitulo3`. Cada una parte de `develop` y se revisa antes de integrarla. Figma y capítulo IV quedan fuera de estos cambios.

<a id="solucion"></a>
## 1.2. Solution Profile

MISTHY propone tres experiencias complementarias: una aplicación para el ciudadano, una web de acceso y recuperación desde otro dispositivo y Misthy Command para coordinar incidentes dentro de una organización. Para una primera versión realizable por un desarrollador, se prioriza la experiencia web adaptable y el ciclo **registrar → compartir de forma controlada → coordinar → consultar seguimiento → exportar**.

Se conserva como propuesta técnica Vue 3 + Vite, API Node.js y SQL Server. Flutter queda en la visión móvil futura; Firebase o Supabase son alternativas por evaluar, no dos dependencias simultáneas ya elegidas. El PDF de referencia solicita otro backend para su curso, pero esa obligación académica no se aplica al proyecto personal por instrucción del autor.

<a id="problematica"></a>
### 1.2.1. Antecedentes y problemática

#### Contexto documentado de Perú

El INEI reporta, para julio–diciembre de 2025, una victimización de **23.9 %** y una percepción de inseguridad de **83.7 %** en la población urbana de 15 años o más. Son estimaciones preliminares de ENAPRES; el módulo tiene una muestra anual de 28 624 viviendas. La percepción se refiere a la posibilidad de sufrir un delito en los siguientes doce meses; no equivale a victimización ni a una probabilidad individual calculada. Estos datos contextualizan el problema nacional, no estiman la incidencia específica de Villa El Salvador [R1].

OSIPTEL informó **1 462 487 reportes de celulares robados durante 2025**, recibidos por las operadoras. Son reportes administrativos nacionales; no representan necesariamente víctimas únicas ni denuncias policiales [R2]. La pérdida del teléfono afecta también el acceso a contactos y a información almacenada, una dependencia que MISTHY debe investigar con usuarios.

La extorsión exige mirar más allá del robo. En octubre de 2024, la Defensoría del Pueblo solicitó mejorar la operatividad de la central 111 y permitir el registro de denuncias en SIDPOL para facilitar actuaciones de investigación [R3]. En marzo de 2025 alertó sobre extorsiones a instituciones educativas privadas que ocasionaban suspensión de clases presenciales [R4]. Estos antecedentes documentan afectaciones y necesidades de atención; no constituyen una tasa actual de extorsión para el piloto.

En su informe de gobernabilidad de julio–diciembre de 2025, el INEI registra **84.6 % de desconfianza en la PNP** y **83.5 % en el Poder Judicial**, entre la población de 18 años o más, con datos preliminares de ENAHO y una muestra anual cercana a 37 mil viviendas [R5, cuadro 3]. Se trata de percepción institucional: no prueba inacción de cada policía ni permite calcular una tasa de impunidad.

#### Impunidad, barreras y acceso desigual a la justicia

La preocupación por hechos sin esclarecimiento o sanción forma parte central del problema que motiva MISTHY. En esta versión no se asigna un porcentaje de impunidad: se requeriría seguir una misma cohorte de casos desde denuncia hasta resolución firme. Dividir denuncias de un año entre sentencias del mismo año produciría una comparación inválida si corresponden a expedientes y plazos distintos.

La afirmación «solo hay justicia para quien tiene dinero» se trabaja como una **percepción de desigualdad y una hipótesis de barreras de acceso**, no como hecho universal. Las entrevistas explorarán tiempo disponible, gastos de traslado, comprensión de procedimientos, acceso a orientación, seguimiento y temor a represalias. El producto buscará reducir fricciones informativas sin atribuir corrupción o culpabilidad a personas sin evidencia.

#### Antecedente ilustrativo: Liceo Naval y nueva denuncia en centro juvenil

El autor aportó dos noticias. América Noticias informó sobre una audiencia de esclarecimiento de hechos del 9 de octubre de 2026 en la investigación por presunta agresión sexual vinculada al Liceo Naval Almirante Guise [R6]. Perú21 informó el 8 de octubre sobre una nueva denuncia de presunta agresión contra un adolescente internado en un centro juvenil y sobre medidas de protección comunicadas por Pronacej [R7]. Son episodios relacionados pero distintos; no deben confundirse sus víctimas ni sus actuaciones.

Como contraste primario, el 17 de septiembre de 2026 la Defensoría señaló preocupación por la falta de atención oportuna de la institución educativa ante alertas y solicitó protección integral y determinación de responsabilidades [R8]. Esto respalda examinar fallas de protección y seguimiento. **Las fuentes revisadas no acreditan una sentencia definitiva, impunidad consumada ni favoritismo económico demostrado.**

La lección de producto es preservar la cronología, registrar a quién se comunicó una alerta y diferenciar recepción, actuación y resultado. No se reproducen identidades, imágenes ni detalles gráficos de menores. El piloto no incluye investigación de violencia sexual infantil ni manejo de esos expedientes; su eventual abordaje exigiría un diseño especializado.

#### Análisis 5W + 2H

| Pregunta | Aplicación a MISTHY |
|---|---|
| Who — ¿Quién? | Personas adultas que necesitan apoyo ante incidentes y responsables de organizaciones vecinales o pequeños negocios que coordinan su atención. |
| What — ¿Qué? | Dificultad para pedir apoyo, conservar información sensible y conocer qué gestiones se realizaron ante un robo, amenaza o presunta extorsión. |
| Where — ¿Dónde? | Perú como contexto; un sector de Villa El Salvador como piloto propuesto, aún sin organización aliada confirmada. |
| When — ¿Cuándo? | Antes del incidente al preparar contactos; durante al solicitar ayuda; después al conservar información y seguir gestiones. |
| Why — ¿Por qué? | Hipótesis: información dispersa, pérdida de acceso al teléfono, coordinación informal, barreras de atención y desconfianza dificultan la continuidad. |
| How — ¿Cómo ocurre hoy? | Hipótesis por validar: llamadas, mensajes, visitas presenciales y documentos separados sin una cronología compartida controlada. |
| How much — ¿Cuánto? | Las fuentes nacionales dimensionan el contexto. Costos por víctima, tiempos locales y disposición de pago no se han medido; no se inventan estimaciones. |

#### Objetivo y alcance inicial

**Objetivo general:** validar si una plataforma accesible de registro privado, coordinación y seguimiento ayuda a las personas a organizar un incidente y comprender el estado real de las gestiones realizadas.

| Dentro del MVP propuesto | Fuera del compromiso inicial |
|---|---|
| Registro privado de robo, amenaza o presunta extorsión y cronología. | Investigar delitos, determinar culpabilidad o garantizar justicia. |
| Red de confianza con invitaciones y consentimiento. | Publicar acusaciones, teléfonos de presuntos autores o identidades de víctimas. |
| Solicitud de apoyo y estado verificable de notificación. | Garantizar despacho policial o llegada de ayuda en un tiempo fijo. |
| Seguimiento interno y referencia externa añadida por el usuario. | Consultar expedientes oficiales sin acuerdo o integración autorizada. |
| Archivos privados y exportación con metadatos de procedencia. | Certificar judicialmente pruebas o prometer admisibilidad del PDF. |
| Recuperación de acceso desde otro equipo y revocación de sesiones. | Bloquear el sistema operativo, impedir apagado o rastrear un teléfono apagado. |
| Ubicación consentida con hora y precisión; mapa comunitario moderado. | Seguimiento encubierto, predicción de culpabilidad o localización garantizada sin conexión. |

Los avisos de extorsión son privados por defecto y no se publican en el mapa. Revocar sesiones MISTHY no equivale a bloquear físicamente el teléfono. La plataforma admite reportes sin adjuntos; no obliga a la víctima a reunir pruebas para pedir apoyo. La información pública se minimiza y nunca se presenta como garantía de seguridad de una zona.

<a id="lean"></a>
### 1.2.2. Lean UX Process

Se aplica Lean UX como proceso de aprendizaje: declarar supuestos, escoger los de mayor riesgo, probarlos con entrevistas y tareas controladas y ajustar el alcance. A continuación se documenta una propuesta inicial, no resultados de experimentos.

<a id="problem-statement"></a>
#### 1.2.2.1. Lean UX Problem Statement

El ámbito de seguridad ciudadana y apoyo posterior a incidentes en Perú dispone de canales de denuncia y herramientas de localización o comunicación. La hipótesis de brecha de MISTHY es que las personas afectadas y quienes coordinan apoyo local todavía necesitan continuidad entre solicitar ayuda, organizar información privada y conocer las actuaciones realizadas, incluso cuando se pierde el dispositivo habitual. MISTHY abordará esa brecha mediante un registro privado de incidentes, una red de confianza y una cronología compartida con acceso limitado. El foco inicial serán adultos de un sector de Villa El Salvador y responsables de organizaciones locales participantes. Se considerará que la propuesta obtiene señales de éxito cuando, en un piloto de 60 días, al menos 40 de 50 participantes invitados activen su red de apoyo, 8 de 10 personas completen las tareas de recuperación evaluadas y 2 organizaciones acepten continuar un piloto tras probar la coordinación. Estas metas son objetivos de validación, no resultados observados ni garantías de protección.

<a id="assumptions"></a>
#### 1.2.2.2. Lean UX Assumptions

| Tipo | ID | Creencia por validar |
|---|---|---|
| Business | BA01 | Existe interés en una herramienta local que dé continuidad a alertas y gestiones. |
| Business | BA02 | Una organización vecinal o un pequeño negocio puede financiar herramientas de coordinación sin cobrar por el acceso esencial de la víctima. |
| Business | BA03 | Un único desarrollador puede sostener un MVP web acotado; una central humana permanente requeriría recursos adicionales. |
| Business Outcome | BO01 | La activación de contactos de confianza favorece el uso recurrente del producto. |
| Business Outcome | BO02 | Una cronología comprensible aumenta la intención de continuidad de organizaciones piloto. |
| Business Outcome | BO03 | Una recuperación de acceso exitosa aumenta la confianza en el servicio. |
| User | UA01 | Los adultos participantes disponen de un navegador propio o prestado, aunque con diferentes habilidades digitales. |
| User | UA02 | Los responsables locales necesitan separar avisos privados de información comunitaria publicable. |
| User | UA03 | El miedo a represalias y la desconfianza pueden limitar el registro de extorsiones. |
| User Outcome and Benefit | UO01 | Las personas valoran saber si alguien recibió una alerta y qué sigue pendiente. |
| User Outcome and Benefit | UO02 | Las personas necesitan conservar su información sin divulgarla indiscriminadamente. |
| User Outcome and Benefit | UO03 | Los coordinadores valoran reducir duplicidad y conservar responsables y fechas. |
| Feature | FA01 | Una red de confianza con aceptación explícita facilita preparar apoyo. |
| Feature | FA02 | Una alerta con estado de entrega verificable permite comprender su alcance real. |
| Feature | FA03 | Un registro privado de amenazas y adjuntos facilita ordenar información. |
| Feature | FA04 | Una cronología con responsable, estado y referencia externa facilita seguimiento. |
| Feature | FA05 | Una recuperación con LLAVE MISTHY y revocación de sesiones facilita recuperar control de la cuenta. |
| Feature | FA06 | Una exportación privada con procedencia reduce el esfuerzo de preparar información para compartir. |
| Feature | FA07 | Un mapa de avisos moderados y sin identidades ayuda a consultar el entorno. |

<a id="hypotheses"></a>
#### 1.2.2.3. Lean UX Hypothesis Statements

Una hipótesis por cada Feature Assumption; todos los umbrales son propuestas de prueba. Día 0 será la fecha de inicio del piloto una vez aprobado, no la fecha de este documento.

| ID / trazabilidad | Enunciado | Experimento y criterio propuesto |
|---|---|---|
| H01 / FA01, BO01, UA01, UO01 | Creemos que aumentará la activación si los ciudadanos preparan su apoyo con una red de contactos que aceptan participar. | Al día 30, ≥40/50 invitados tienen al menos un contacto aceptado; contar usuarios únicos. |
| H02 / FA02, BO01, UA01, UO01 | Creemos que aumentará la confianza de uso si los ciudadanos distinguen envío, entrega y lectura mediante estados verificables. | Al día 45, ≥8/10 participantes interpretan correctamente tres estados en un simulacro sin ayuda del moderador. |
| H03 / FA03, BO01, UA03, UO02 | Creemos que aumentará la utilidad percibida si los ciudadanos organizan amenazas con un registro privado y adjuntos opcionales. | Al día 45, ≥8/10 completan un caso ficticio en ≤5 min sin exponer datos; ≥8/10 comprenden quién puede consultarlo. |
| H04 / FA04, BO02, UA02, UO03 | Creemos que aumentará la continuidad del piloto si los coordinadores conocen responsable y próxima actuación mediante una cronología de seguimiento. | Al día 60, ≥4/5 coordinadores completan una tarea de seguimiento; ≥2 organizaciones aceptan por escrito continuar evaluando. |
| H05 / FA05, BO03, UA01, UO02 | Creemos que aumentará la confianza si los ciudadanos recuperan el control desde otro equipo mediante una llave y revocación de sesiones. | Al día 45, ≥8/10 completan el ejercicio en ≤3 min con llave disponible; registrar fallos y ausencia de llave por separado. |
| H06 / FA06, BO02, UA02, UO02 | Creemos que aumentará la utilidad para los dos segmentos si preparan una copia ordenada mediante exportación con metadatos. | Al día 60, ≥8/10 participantes encuentran fecha, origen y estado de los datos en ≤2 min; sin medir admisibilidad judicial. |
| H07 / FA07, BO01, UA01, UO01 | Creemos que mejorará la consulta responsable del entorno si los ciudadanos distinguen avisos moderados y antigüedad mediante un mapa sin identidades. | Al día 60, ≥8/10 interpretan correctamente la antigüedad y no confunden ausencia de avisos con ausencia de riesgo. |

Una muestra pequeña proporciona aprendizaje cualitativo, no inferencia representativa sobre todo Perú. Para cada prueba se registra numerador, denominador, abandonos, permisos y contexto. Cero participantes significa «sin datos», nunca 0 % de éxito.

<a id="canvas"></a>
#### 1.2.2.4. Lean UX Canvas

| Bloque | Contenido de trabajo |
|---|---|
| 1. Business problem | Falta de continuidad y visibilidad entre alerta, registro privado y seguimiento de gestiones. |
| 2. Business outcomes | Activación, comprensión del servicio e intención de continuidad del piloto; H01–H07. |
| 3. Users | S1: ciudadanos adultos. S2: responsables de coordinación local. |
| 4. User outcomes and benefits | Preparar apoyo, reducir incertidumbre, conservar privacidad y organizar actuaciones. |
| 5. Solutions | Red de confianza, alertas trazables, registro privado, cronología, recuperación, exportación y mapa moderado. |
| 6. Hypotheses | H01–H07, cada una vinculada a un supuesto de funcionalidad. |
| 7. Most important thing to learn first | Si las personas confían en registrar información sensible y entienden que MISTHY no equivale a una denuncia formal ni garantiza respuesta oficial. |
| 8. Least work to learn | Entrevistas semiestructuradas con 3–5 personas por segmento y pruebas con casos ficticios; luego un prototipo de registro/seguimiento. Sin datos reales de víctimas para demostraciones públicas. |

<a id="segmentos"></a>
## 1.3. Segmentos objetivo

| Característica | S1 — Ciudadanos adultos | S2 — Responsables de coordinación local |
|---|---|---|
| Delimitación inicial | Personas de 18 años o más que viven, trabajan o se desplazan por el sector piloto de VES. | Adultos con responsabilidad verificable de coordinar apoyo en una junta vecinal, asociación o pequeño negocio del sector. |
| Diversidad a incluir | Distintos géneros, ocupaciones, habilidades digitales y condiciones de accesibilidad; no se presupone un nivel de ingresos. | Coordinadores con diferentes recursos, horarios y experiencia digital; se distingue usuario operativo de comprador. |
| Necesidad hipotética | Pedir apoyo, conservar información y entender seguimiento sin perder privacidad. | Recibir información suficiente, asignar responsables y evitar pérdida de continuidad. |
| Contexto de uso | Teléfono propio, navegador prestado o PC; conectividad variable. | PC o teléfono; coordinación durante horarios acordados, sin asumir atención 24/7. |
| Comprador posible | Persona interesada en funciones adicionales; funciones esenciales no condicionadas al pago. | Organización que acepta un piloto y eventualmente contrata coordinación. |
| Sustento y límite | R1 y R2 documentan el contexto nacional; no demuestran demanda ni tamaño de mercado local. | R3–R5 justifican investigar atención y confianza; no cuantifican organizaciones disponibles ni intención de compra. |

Se selecciona VES para mantener el trabajo de campo acotado a Lima, donde reside el fundador. La elección es operativa, no una afirmación de que sea el distrito con más delitos. Municipalidades, universidades, transportistas y escuelas son posibles expansiones; no se mezclan con los dos segmentos del primer estudio. Menores de edad quedan fuera del reclutamiento inicial.

<a id="referencias"></a>
## Referencias y evidencia pendiente

Referencias consultadas el 9 de octubre de 2026. Los antecedentes periodísticos están atribuidos y no se usan como sentencia judicial.

- **R1.** Instituto Nacional de Estadística e Informática. (2026, febrero). *Estadísticas de seguridad ciudadana: julio–diciembre 2025* (gráfico 1 y notas metodológicas, p. 1). https://www.inei.gob.pe/media/MenuRecursivo/boletines/seguridad_ciudadana_jul_dic_2025.pdf
- **R2.** OSIPTEL. (2026, 15 de enero). *Robos de celulares disminuyeron en 2025, ¿cuánto se reportó ante las empresas operadoras?* https://www.osiptel.gob.pe/portal-del-usuario/noticias/robos-de-celulares-disminuyeron-en-2025-cu%C3%A1nto-se-report%C3%B3-ante-las-empresas-operadoras/
- **R3.** Defensoría del Pueblo. (2024, 18 de octubre). *Defensoría del Pueblo supervisa operatividad de línea telefónica implementada por PNP para casos de extorsiones* (Nota 268/2024). https://www.defensoria.gob.pe/wp-content/uploads/2024/10/NP-268-2024.pdf
- **R4.** Defensoría del Pueblo. (2025, marzo). *Nota de prensa 055/2025: Extorsión a instituciones educativas privadas*. https://www.defensoria.gob.pe/wp-content/uploads/2025/03/NP-055-2025-Extorsi%C3%B3n-a-instituciones-educativas-privadas.pdf
- **R5.** Instituto Nacional de Estadística e Informática. (2026, febrero). *Perú: Percepción ciudadana sobre gobernabilidad, democracia y confianza en las instituciones. Julio–diciembre 2025* (cuadro 3, p. 6). https://www.inei.gob.pe/media/MenuRecursivo/boletines/boletin_gobernabilidad_julio_diciembre2025.pdf
- **R6.** Silva, K. (2026, 9 de octubre; fecha de la audiencia descrita). *Liceo Naval: Hoy realizan audiencia por presunta agresión sexual*. América Noticias. https://www.americatv.com.pe/noticias/actualidad/liceo-naval-hoy-realizan-audiencia-presunta-agresion-sexual-n523353
- **R7.** Zagaceta, J., y Llanos, K. (2026, 8 de octubre). *Alumno de Liceo Naval fue agredido en las duchas de Maranguita por su propio compañero*. Perú21. https://peru21.pe/policiales/alumno-de-liceo-naval-fue-agredido-en-las-duchas-de-maranguita-por-su-propio-companero/
- **R8.** Defensoría del Pueblo. (2026, 17 de septiembre). *Defensoría del Pueblo solicita atención integral para adolescente víctima de violencia en la Institución Educativa Liceo Naval*. https://www.defensoria.gob.pe/defensoria-del-pueblo-solicita-atencion-integral-para-adolescente-victima-de-violencia-en-la-institucion-educativa-liceo-naval/
- **R9.** Universidad Peruana de Ciencias Aplicadas. (2026). *1ASI0730 Aplicaciones Web: Enunciado del trabajo final, v1*. Archivo aportado por el autor; pp. 5 y 8–15 utilizadas únicamente como referencia metodológica.

**Pendientes reales:** seleccionar sector y organización piloto; realizar entrevistas; validar hipótesis, costos y capacidad operativa; revisar privacidad y seguridad antes de recibir incidentes reales. No son tareas declaradas como realizadas.
