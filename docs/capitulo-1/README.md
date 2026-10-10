# Capítulo I: Introducción

**Proyecto personal:** MISTHY («Tu ciudad te cuida»). **Autor:** Christoper Steven Rivas Castillo — [CODERT0PH](https://github.com/CODERT0PH). **Versión:** 0.2.0. **Fecha de corte:** 10 de octubre de 2026, Lima.

Este capítulo presenta la startup, el problema que motiva MISTHY, la solución completa (Misthy App, Misthy Web y Misthy Command) y sus hipótesis iniciales. Los nombres de productos, módulos, personas y user goals son los mismos que usa el [Capítulo IV · Product Design](../capitulo-4/README.md) y el [archivo Figma](https://www.figma.com/design/MNhixqFUFzjBqxVnzp5dTJ), para que los cuatro capítulos se lean como un solo documento. El enunciado de Aplicaciones Web aportado por el autor se usa como guía de estructura; este es un proyecto propio.

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

MISTHY es un SaaS de seguridad ciudadana 360° para Lima, con piloto en Villa El Salvador (VES). No es «otra app de botón de pánico»: es la capa de datos y respuesta en tiempo real entre el ciudadano, su red de confianza, la comunidad y las autoridades locales (serenazgo y comisarías). El nombre y la marca se inspiran en el volcán Misti: *«como el Misti vigila Arequipa, Misthy vigila tu cuadra»*.

La iniciativa responde a cuatro dolores de Lima que el fundador identificó y que el producto aborda módulo por módulo:

| Dolor | Respuesta de MISTHY | Módulos |
|---|---|---|
| Robo de celular al paso | Ubicación, sirena, bloqueo remoto y borrado selectivo desde cualquier navegador con la Llave Misthy; rastreo por la Red Mesh cuando el equipo no tiene datos. | M4 Anti-Robo, Misthy Web |
| Asalto con coacción | PIN de coacción que abre una pantalla señuelo mientras graba y alerta en silencio. | M5 PIN de Coacción, M2 Pánico |
| Persecución o acoso | Falso Acompañante con voz IA, Modo Viaje Seguro y rutas a Puntos Misthy (comercios refugio). | M3, M8, M1 |
| Impunidad y desorientación | Expediente probatorio PDF (fotos, audio, GPS, timestamps) enviado a la comisaría o al serenazgo, con seguimiento visible. | M6 Bóveda, Misthy Web, Misthy Command |

**Misión:** que cualquier persona pueda pedir ayuda, proteger su información y su celular, y llegar a la comisaría con evidencia ordenada, aunque le hayan robado el teléfono.

**Visión:** ser la infraestructura de seguridad ciudadana de Latinoamérica, empezando por un sector de VES y creciendo con municipalidades, juntas vecinales y universidades.

**Principios** (los mismos del capítulo IV): claridad primero, honestidad de estados («Solicitud enviada → Pendiente → Confirmado por el dispositivo / No se pudo ejecutar»), acción en un paso, inclusión y consistencia entre productos. A ellos se suman privacidad por defecto, trazabilidad de acciones y atención crítica que nunca se prioriza por plan de pago.

**Identidad:** púrpura `#6D28D9`, azul `#2563EB` y azul noche `#0F172A`, con Manrope e Inter. El detalle visual, los tokens y los componentes están en el [Capítulo IV, 4.1](../capitulo-4/README.md#41-style-guidelines).

**Modelo de negocio (freemium + B2B/B2G):**

| Cliente | Plan (como aparece en el landing del capítulo IV) | Precio referencial / mes |
|---|---|---|
| Ciudadano | Misthy Free → Misthy Pro | Gratis / S/ 9.90–14.90 |
| Juntas vecinales y condominios | Organizaciones | S/ 150–350 por cuadrante |
| Universidades | Organizaciones | S/ 1 200–3 000 por campus |
| Municipalidades | Misthy Command | S/ 4 500–8 500 por distrito |

Los precios son referenciales y se validarán en el piloto. Las funciones esenciales de emergencia (pánico, acceso de emergencia, bloqueo y aviso a contactos) son gratuitas. La empresa aún no está constituida y no existe todavía un convenio firmado con la PNP ni con una municipalidad.

<a id="autor"></a>
### 1.1.2. Perfil del autor y organización del trabajo

**Christoper Steven Rivas Castillo (CODERT0PH)** es el fundador y único responsable de MISTHY. Estudia Ingeniería de Software en la UPC (séptimo ciclo) y reside en Lima. Trabaja con JavaScript, Vue, Vite, C#, Java y Python; bases de datos relacionales y MongoDB; Git/GitHub; ciberseguridad y contenido educativo.

Asume las decisiones de producto, investigación, diseño, documentación, desarrollo y validación. Usa asistentes de IA como herramientas de apoyo; las entrevistas y la validación con usuarios reales siguen siendo trabajo pendiente del autor.

La documentación se organiza en una rama por capítulo: `feature-capitulo1`, `feature-capitulo2`, `feature-capitulo3` y `feauture-capitulo4` (Product Design, con los diseños de Figma).

<a id="solucion"></a>
## 1.2. Solution Profile

MISTHY es un ecosistema de tres productos que comparten la misma API, el mismo design system y el mismo lenguaje:

```
Misthy App (Flutter) ────┐
Misthy Web (Vue 3 + Vite) ┼─► API REST (Node.js) ─► SQL Server (usuarios, suscripciones, pagos)
Misthy Command (Vue 3) ───┘        └──► Firebase o Supabase (tiempo real) · MongoDB en fase 2
```

**A. Misthy App (ciudadano, móvil, Flutter)**

| # | Módulo | Funciones clave |
|---|---|---|
| M1 | Mapa Vivo | Mapa de calor de delitos verificados, pines comunitarios, alerta de voz/vibración al entrar en zona roja, Puntos Misthy (comercios refugio). |
| M2 | Pánico | Triple pulso del botón de volumen, gesto en smartwatch, grabación de audio cifrada de 10 min, GPS en vivo a contactos y a la central. |
| M3 | Modo Viaje Seguro | Escáner de placa de taxi/moto, geocerca de desvío, escalamiento automático a contactos si no respondes en 20 s. |
| M4 | Anti-Robo | Rastreo por Red Mesh Bluetooth sin conexión, alarma remota al 100 % de volumen, fotos stealth, detección de «jalón» por sensores, bloqueo y wipe con llave privada. |
| M5 | PIN de Coacción | PIN falso que abre una pantalla señuelo mientras activa un Lockdown silencioso en segundo plano. |
| M6 | Bóveda | Documentos y credenciales cifrados (AES-256) y expediente probatorio PDF exportable. |
| M7 | Comunidad | Reportes verificados, puntos, badges y ranking vecinal. |
| M8 | Falso Acompañante | Llamada o videollamada simulada con voz IA para disuasión. |

**B. Misthy Web (ciudadano, web responsive, mobile-first)** — diseñada en el capítulo IV (4.4) con los flujos UF1–UF3.

- **Acceso de emergencia** (`misthy.app/emergencia`): correo + **Llave Misthy** (clave secreta de 12–16 caracteres). La bóveda completa exige además 2FA.
- **Panel de recuperación:** Mi dispositivo (conexión, batería, última ubicación), Ubicación (mapa e historial), **Bloquear** (Lockdown), **Sirena**, **Bóveda** (congelar o borrar), **Avisar a PNP** (expediente) y **Contactos**.
- Cada orden remota muestra su estado real: *Solicitud enviada*, *Pendiente de conexión*, *Confirmado por el dispositivo* o *No se pudo ejecutar · Reintentar*.

**C. Misthy Command (municipalidades y serenazgo, desktop)** — diseñado en el capítulo IV con los flujos UF4–UF6.

| Módulo | Función |
|---|---|
| Monitor | Mapa distrital y cola de alertas por severidad S1–S5. |
| Despachar | Asignar el sereno o la unidad más cercana y seguir su estado (en camino, en sitio, cerrada). |
| Reportes | Verificar o descartar reportes comunitarios con evidencia. |
| Expedientes PNP | Bandeja de expedientes PDF, revisión y exportación para comisarías. |
| Analítica | Patrones por hora, zona y tipo de delito; predicción de riesgo y reportes. |
| Administración | Roles (operador, supervisor, admin), cobertura y facturación. |

**Límites técnicos que se comunican con honestidad:** el botón de encendido no se puede anular en Android 12+ ni en iOS; la alternativa viable en Android es un modo kiosk que pide la Llave Misthy para abrir el menú de apagado (Device Admin), y en iOS la protección es más limitada. Un teléfono apagado no transmite GPS: se usa la última ubicación, la batería y el vector de movimiento enviados antes del apagado, y la Red Mesh cuando el equipo emite Bluetooth sin datos. MISTHY no garantiza recuperar el equipo, no reemplaza la denuncia formal y no determina culpables.

<a id="problematica"></a>
### 1.2.1. Antecedentes y problemática

#### Contexto documentado de Perú

El INEI reporta, para julio–diciembre de 2025, una victimización de **23.9 %** y una percepción de inseguridad de **83.7 %** en la población urbana de 15 años o más. Son estimaciones preliminares de ENAPRES (muestra anual de 28 624 viviendas). La percepción se refiere a la posibilidad de sufrir un delito en los siguientes doce meses; no equivale a victimización [R1].

OSIPTEL informó **1 462 487 reportes de celulares robados durante 2025**, recibidos por las operadoras. Son reportes administrativos; no necesariamente víctimas únicas ni denuncias policiales [R2]. Perder el teléfono significa perder también contactos, cuentas, documentos y el propio canal para pedir ayuda: por eso Misthy Web existe como vía de recuperación desde un equipo prestado.

La extorsión exige mirar más allá del robo. En octubre de 2024 la Defensoría del Pueblo pidió mejorar la operatividad de la central 111 y permitir el registro de denuncias en SIDPOL [R3]. En marzo de 2025 alertó sobre extorsiones a instituciones educativas privadas que obligaron a suspender clases presenciales [R4].

En su informe de gobernabilidad de julio–diciembre de 2025, el INEI registra **84.6 % de desconfianza en la PNP** y **83.5 % en el Poder Judicial** entre la población de 18 años o más [R5, cuadro 3]. Es percepción institucional, no una tasa de impunidad.

#### Impunidad, barreras y acceso desigual a la justicia

La preocupación por hechos sin esclarecimiento ni sanción es central en MISTHY. No se asigna un porcentaje de impunidad: calcularlo exigiría seguir una misma cohorte de casos desde la denuncia hasta la resolución firme. La idea de que «solo hay justicia para quien tiene dinero» se trabaja como percepción de desigualdad y como hipótesis de barreras de acceso (tiempo, traslados, comprensión de procedimientos, seguimiento y temor a represalias). El expediente probatorio y el seguimiento visible buscan reducir esas barreras.

#### Antecedente ilustrativo: Liceo Naval y nueva denuncia en centro juvenil

América Noticias informó sobre una audiencia del 9 de octubre de 2026 en la investigación por presunta agresión sexual vinculada al Liceo Naval Almirante Guise [R6]. Perú21 informó el 8 de octubre sobre una nueva denuncia de presunta agresión contra un adolescente internado en un centro juvenil [R7]. El 17 de septiembre de 2026 la Defensoría señaló falta de atención oportuna de la institución educativa ante alertas y pidió protección integral [R8]. Las fuentes no acreditan una sentencia definitiva. La lección de producto es preservar la cronología, registrar a quién se comunicó cada alerta y diferenciar recepción, actuación y resultado. El piloto no maneja casos de menores de edad.

#### Análisis 5W + 2H

| Pregunta | Aplicación a MISTHY |
|---|---|
| Who — ¿Quién? | Ciudadanos adultos como Lucía (víctima de robo de celular), operadores de serenazgo como Carlos y supervisoras de gestión comunitaria como Rosa. |
| What — ¿Qué? | Robo de celular, asalto con coacción, acoso y extorsión, seguidos de desorientación: sin teléfono, sin evidencia ordenada y sin saber si alguien atiende. |
| Where — ¿Dónde? | Lima; piloto en un sector de Villa El Salvador, por sus sectores numerados y juntas vecinales organizadas. |
| When — ¿Cuándo? | Antes (configurar Llave Misthy, contactos y bóveda), durante (pánico, viaje seguro, PIN de coacción) y después (recuperación, expediente PNP y seguimiento). |
| Why — ¿Por qué? | Al perder el teléfono se pierde el canal para pedir ayuda; la información queda dispersa y la coordinación con serenazgo y PNP es informal. |
| How — ¿Cómo ocurre hoy? | Llamadas desde teléfonos prestados, visitas a la comisaría sin evidencia, mensajes sueltos y herramientas de localización que no conectan con la autoridad local. |
| How much — ¿Cuánto? | Las cifras nacionales dimensionan el contexto (R1, R2, R5). Tiempos de respuesta locales y disposición de pago se medirán en el piloto. |

#### Objetivo y alcance

**Objetivo general:** validar que MISTHY reduce la desorientación de una persona ante un robo o una amenaza, protege su información y su equipo, y acorta el tiempo de respuesta del serenazgo en un sector piloto de VES.

| Fase | Alcance | Productos y módulos |
|---|---|---|
| MVP (semanas 1–4) | Pánico, Mapa Vivo y anti-robo básico en la app; acceso de emergencia, bloqueo remoto, sirena, bóveda y aviso a la PNP en la web. | M1, M2, M4 (sirena, bloqueo, fotos), M6; Misthy Web completa |
| Piloto (semanas 5–8) | 50–100 usuarios vía 2–3 juntas vecinales de un sector; demo de Command con datos reales para la municipalidad. | Misthy Command (Monitor, Despachar, Reportes, Expedientes PNP), M7 |
| Fase 2 | Funciones que requieren más investigación técnica o alianzas. | M3, M5, M8, Red Mesh de M4, Analítica predictiva, integración formal con PNP |

Reglas que se mantienen en todas las fases: los reportes de extorsión son privados por defecto y nunca se publican en el mapa; el ciudadano puede pedir ayuda sin adjuntar pruebas; ninguna orden remota se muestra como ejecutada sin confirmación del dispositivo; el mapa nunca se presenta como garantía de que una zona es segura.

<a id="lean"></a>
### 1.2.2. Lean UX Process

Se aplica Lean UX como ciclo de aprendizaje: declarar supuestos, escoger los de mayor riesgo, probarlos con entrevistas y con los prototipos del capítulo IV, y ajustar el alcance. Lo que sigue es la propuesta inicial; los resultados se registrarán en el piloto.

<a id="problem-statement"></a>
#### 1.2.2.1. Lean UX Problem Statement

Los servicios de seguridad ciudadana en Lima ofrecen canales de denuncia y existen herramientas para localizar teléfonos, pero no conectan al ciudadano con su red, con el serenazgo y con la comisaría en el momento del incidente ni después. Hemos observado que, cuando a una persona le roban el celular o la amenazan, pierde su canal para pedir ayuda, su información queda expuesta o dispersa y no sabe si alguien está atendiendo su caso. MISTHY abordará esta brecha con una app de protección personal, una web de recuperación accesible desde cualquier navegador y un panel de monitoreo y despacho para municipalidades. El foco inicial son adultos de un sector de Villa El Salvador, los operadores de serenazgo y las juntas vecinales del sector. Sabremos que vamos por buen camino si, en un piloto de 60 días, al menos 40 de 50 participantes configuran su Llave Misthy y un contacto aceptado, 8 de 10 completan el bloqueo remoto desde un navegador prestado en 3 minutos o menos y una municipalidad acepta continuar con Misthy Command.

<a id="assumptions"></a>
#### 1.2.2.2. Lean UX Assumptions

| Tipo | ID | Creencia por validar |
|---|---|---|
| Business | BA01 | Existe demanda de una herramienta local que una alerta, recuperación del celular y seguimiento con la autoridad. |
| Business | BA02 | Las municipalidades pagarán por Misthy Command si reduce el tiempo de despacho del serenazgo. |
| Business | BA03 | Juntas vecinales y universidades financiarán planes de organización sin cobrar a la víctima las funciones esenciales. |
| Business Outcome | BO01 | Configurar Llave Misthy y contactos aumenta la retención de la app. |
| Business Outcome | BO02 | Un monitor con severidad S1–S5 y despacho reduce el tiempo de respuesta y aumenta la intención de contratar. |
| Business Outcome | BO03 | Una recuperación remota exitosa convierte usuarios Free en Misthy Pro. |
| User | UA01 | Tras un robo, la persona consigue un navegador prestado (celular o PC) y recuerda su correo y su Llave Misthy. |
| User | UA02 | Los operadores de serenazgo necesitan priorizar alertas por severidad y ver la evidencia junto al mapa. |
| User | UA03 | El miedo a represalias limita reportar extorsiones si el reporte no es privado. |
| User Outcome and Benefit | UO01 | La víctima valora saber que su orden de bloqueo se ejecutó y que sus contactos recibieron la alerta. |
| User Outcome and Benefit | UO02 | La víctima valora llegar a la comisaría con un expediente ordenado. |
| User Outcome and Benefit | UO03 | Las supervisoras comunitarias valoran publicar solo reportes verificados en el mapa. |
| Feature | FA01 | Una red de confianza con aceptación explícita facilita preparar apoyo. |
| Feature | FA02 | Alertas de pánico con estado de entrega verificable dan confianza. |
| Feature | FA03 | Un registro privado con adjuntos opcionales facilita ordenar amenazas y extorsiones. |
| Feature | FA04 | Una cronología con responsable, estado y referencia externa facilita el seguimiento. |
| Feature | FA05 | El acceso de emergencia con Llave Misthy y el bloqueo remoto permiten proteger el equipo desde otro dispositivo. |
| Feature | FA06 | El expediente PDF con procedencia reduce el esfuerzo de denunciar ante la PNP. |
| Feature | FA07 | Un Mapa Vivo con reportes verificados y alerta de zona roja ayuda a moverse con más información. |
| Feature | FA08 | Un monitor con cola por severidad y despacho al sereno más cercano reduce el tiempo de respuesta. |
| Feature | FA09 | Borrar o congelar la bóveda con 2FA protege documentos sensibles si desbloquean el equipo. |
| Feature | FA10 | Modo Viaje Seguro, PIN de coacción y Falso Acompañante aumentan la sensación de control en trayectos de riesgo. |
| Feature | FA11 | La Red Mesh y la detección de «jalón» mejoran la localización de equipos robados sin datos. |
| Feature | FA12 | Puntos, badges y ranking vecinal aumentan la cantidad de reportes con evidencia. |

<a id="hypotheses"></a>
#### 1.2.2.3. Lean UX Hypothesis Statements

Una hipótesis por cada Feature Assumption. Día 0 es el inicio del piloto. Los umbrales son metas de prueba.

| ID / trazabilidad | Enunciado | Experimento y criterio propuesto |
|---|---|---|
| H01 / FA01, BO01, UO01 | Creemos que aumentará la activación si los ciudadanos preparan una red de contactos que acepta participar. | Al día 30, ≥40/50 invitados tienen al menos un contacto aceptado. |
| H02 / FA02, BO01, UO01 | Creemos que aumentará la confianza si el ciudadano distingue envío, entrega y lectura de su alerta de pánico. | Al día 45, ≥8/10 interpretan correctamente los estados en un simulacro. |
| H03 / FA03, UA03 | Creemos que aumentarán los reportes de extorsión si el registro es privado y no exige pruebas. | Al día 45, ≥8/10 registran un caso ficticio en ≤5 min y entienden quién puede verlo. |
| H04 / FA04, BO02 | Creemos que aumentará la continuidad si ciudadano y operador ven responsable y próxima actuación. | Al día 60, ≥4/5 operadores completan una tarea de seguimiento. |
| H05 / FA05, BO03, UA01, UO01 | Creemos que Lucía recuperará el control si puede bloquear su celular desde un navegador prestado (UF1). | Al día 45, ≥8/10 completan el bloqueo en ≤3 min con el prototipo de Misthy Web. |
| H06 / FA06, UO02 | Creemos que más víctimas iniciarán la denuncia si envían el expediente a la comisaría desde el panel (UF2). | Al día 60, ≥8/10 envían el expediente sin ayuda y encuentran fecha, origen y estado de cada evidencia. |
| H07 / FA07, UO03 | Creemos que el ciudadano se informará mejor con un Mapa Vivo verificado que no confunde ausencia de reportes con ausencia de riesgo. | Al día 60, ≥8/10 interpretan bien antigüedad y nivel de una zona. |
| H08 / FA08, BO02, UA02 | Creemos que el serenazgo responderá más rápido si Carlos ve la cola por severidad y despacha al sereno más cercano (UF4). | Al día 60, el tiempo mediano entre alerta S5 y despacho baja frente a la línea base medida en la semana 5. |
| H09 / FA09, UO02 | Creemos que Lucía protegerá sus documentos si borra o congela la bóveda con 2FA (UF3). | Al día 45, ≥8/10 completan el borrado o congelamiento en ≤2 min sin borrar archivos por error. |
| H10 / FA10 | Creemos que los usuarios se sentirán más seguros en trayectos si usan Viaje Seguro, PIN de coacción o Falso Acompañante. | En fase 2, ≥60 % de quienes prueben un módulo lo usan de nuevo en 30 días. |
| H11 / FA11 | Creemos que se localizarán más equipos sin datos si la Red Mesh retransmite su señal. | En fase 2, prueba de campo con equipos de prueba: porcentaje de equipos ubicados en 24 h con y sin Mesh. |
| H12 / FA12, UO03 | Creemos que aumentarán los reportes con evidencia si la comunidad recibe puntos y badges al ser verificada (UF5). | Al día 60, la proporción de reportes con evidencia verificada supera la de la semana 5. |

Con muestras pequeñas el aprendizaje es cualitativo. Para cada prueba se registra numerador, denominador, abandonos y contexto; cero participantes significa «sin datos», no 0 %.

<a id="canvas"></a>
#### 1.2.2.4. Lean UX Canvas

| Bloque | Contenido |
|---|---|
| 1. Business problem | Ciudadano, comunidad y autoridad local no están conectados durante ni después de un incidente; al perder el celular se pierde el canal de ayuda. |
| 2. Business outcomes | Activación (Llave + contacto), conversión a Pro, contratos de Misthy Command, menor tiempo de despacho. H01–H12. |
| 3. Users | Lucía Rojas (ciudadana), Carlos Mendoza (operador de serenazgo), Rosa Huamán (supervisora comunitaria). |
| 4. User outcomes and benefits | Proteger el equipo y los documentos, avisar a su gente, llegar a la comisaría con evidencia, atender primero lo más grave, publicar solo información confiable. |
| 5. Solutions | Misthy App (M1–M8), Misthy Web (acceso de emergencia y panel de recuperación) y Misthy Command (monitor, despacho, reportes, expedientes, analítica). |
| 6. Hypotheses | H01–H12, cada una vinculada a un supuesto de funcionalidad. |
| 7. Most important thing to learn first | Si Lucía puede bloquear su celular y avisar a la PNP desde un navegador prestado (UF1, UF2), y si Carlos despacha más rápido con la cola por severidad (UF4). |
| 8. Least work to learn | Pruebas moderadas con los prototipos navegables de Figma (capítulo IV, 4.5) y entrevistas a 3–5 personas por persona objetivo; luego el MVP en un sector. |

<a id="segmentos"></a>
## 1.3. Segmentos objetivo

| Característica | S1 — Ciudadanos (persona: Lucía Rojas) | S2 — Serenazgo y gestión municipal (personas: Carlos Mendoza y Rosa Huamán) |
|---|---|---|
| Delimitación | Adultos de 18 años o más que viven, trabajan o se desplazan por el sector piloto de VES. | Operadores de central de serenazgo, supervisores de gestión comunitaria y enlaces con la PNP de la municipalidad; incluye coordinadores de juntas vecinales. |
| Necesidad | Pedir ayuda, proteger su celular y sus documentos, y denunciar con evidencia aunque le hayan robado el teléfono. | Priorizar alertas, despachar serenos, verificar reportes y entregar expedientes a la comisaría. |
| Contexto de uso | App en su celular; Misthy Web desde un celular prestado o una PC; conectividad variable. | Misthy Command en PC de central, turnos largos, monitores grandes. |
| Comprador | Ciudadano (Misthy Pro) o su organización (junta, universidad). | Municipalidad (Misthy Command), junta vecinal o condominio (plan Organizaciones). |
| Sustento | R1 y R2 dimensionan victimización y robo de celulares. | R3–R5 justifican mejorar atención, coordinación y confianza. |

Se elige VES por sus sectores numerados (cobertura por cuadrantes), sus juntas vecinales organizadas y su tradición de participación vecinal. Universidades, transportistas y otras municipalidades son expansiones posteriores. Menores de edad quedan fuera del piloto.

<a id="referencias"></a>
## Referencias y evidencia pendiente

Referencias consultadas el 9 de octubre de 2026.

- **R1.** Instituto Nacional de Estadística e Informática. (2026, febrero). *Estadísticas de seguridad ciudadana: julio–diciembre 2025*. https://www.inei.gob.pe/media/MenuRecursivo/boletines/seguridad_ciudadana_jul_dic_2025.pdf
- **R2.** OSIPTEL. (2026, 15 de enero). *Robos de celulares disminuyeron en 2025, ¿cuánto se reportó ante las empresas operadoras?* https://www.osiptel.gob.pe/portal-del-usuario/noticias/robos-de-celulares-disminuyeron-en-2025-cu%C3%A1nto-se-report%C3%B3-ante-las-empresas-operadoras/
- **R3.** Defensoría del Pueblo. (2024, 18 de octubre). *Defensoría del Pueblo supervisa operatividad de línea telefónica implementada por PNP para casos de extorsiones* (Nota 268/2024). https://www.defensoria.gob.pe/wp-content/uploads/2024/10/NP-268-2024.pdf
- **R4.** Defensoría del Pueblo. (2025, marzo). *Nota de prensa 055/2025: Extorsión a instituciones educativas privadas*. https://www.defensoria.gob.pe/wp-content/uploads/2025/03/NP-055-2025-Extorsi%C3%B3n-a-instituciones-educativas-privadas.pdf
- **R5.** Instituto Nacional de Estadística e Informática. (2026, febrero). *Perú: Percepción ciudadana sobre gobernabilidad, democracia y confianza en las instituciones. Julio–diciembre 2025*. https://www.inei.gob.pe/media/MenuRecursivo/boletines/boletin_gobernabilidad_julio_diciembre2025.pdf
- **R6.** Silva, K. (2026, 9 de octubre). *Liceo Naval: Hoy realizan audiencia por presunta agresión sexual*. América Noticias. https://www.americatv.com.pe/noticias/actualidad/liceo-naval-hoy-realizan-audiencia-presunta-agresion-sexual-n523353
- **R7.** Zagaceta, J., y Llanos, K. (2026, 8 de octubre). *Alumno de Liceo Naval fue agredido en las duchas de Maranguita por su propio compañero*. Perú21. https://peru21.pe/policiales/alumno-de-liceo-naval-fue-agredido-en-las-duchas-de-maranguita-por-su-propio-companero/
- **R8.** Defensoría del Pueblo. (2026, 17 de septiembre). *Defensoría del Pueblo solicita atención integral para adolescente víctima de violencia en la Institución Educativa Liceo Naval*. https://www.defensoria.gob.pe/defensoria-del-pueblo-solicita-atencion-integral-para-adolescente-victima-de-violencia-en-la-institucion-educativa-liceo-naval/
- **R9.** Universidad Peruana de Ciencias Aplicadas. (2026). *1ASI0730 Aplicaciones Web: Enunciado del trabajo final, v1*. Usado solo como referencia de estructura.

**Pendientes:** confirmar sector y juntas vecinales del piloto, ejecutar entrevistas, probar los prototipos del capítulo IV con usuarios, validar precios y firmar acuerdos con la municipalidad y la comisaría del sector.
