# Product Backlog

| Dato              | Valor                                                              |
| ----------------- | ------------------------------------------------------------------ |
| Producto          | Sistema Inteligente de Monitoreo de Senderos para Apoyo al Rescate |
| Alcance           | MVP académico para una ruta piloto                                 |
| Product Owner     | Manuel, representante del socio formador                           |
| Equipo            | Álvaro, Diego, Lucas y Valeria                                     |
| Versión           | 1.2                                                                |
| Fecha de revisión | 1 de octubre de 2026                                               |

## 1. Forma de estimación

### Story Points — SP

Los SP estiman esfuerzo considerando trabajo, dificultad técnica,
incertidumbre, dependencias y pruebas. Utilizamos la escala Fibonacci:
**1, 2, 3, 5, 8 y 13**.

### Tamaño funcional — TF

El TF representa cuánta funcionalidad aporta cada feature mediante una escala
simplificada del equipo. **No corresponde a un cálculo formal IFPUG de Function
Points.** Si la materia requiere Function Points formales, deberán clasificarse
entradas, salidas, consultas, archivos internos e interfaces externas con la
metodología solicitada por el profesor.

|   TF | Tamaño funcional aproximado                                  |
| ---: | ------------------------------------------------------------ |
|  1–2 | Función pequeña o principalmente técnica                     |
|  3–4 | Función con pocas entradas, salidas o reglas                 |
|  5–6 | Función media con varias operaciones relacionadas            |
|  7–8 | Función amplia con datos, reglas y consultas                 |
| 9–10 | Función transversal con varias pantallas, flujos o entidades |

## 2. Tabla del Product Backlog

### Prioridad alta — indispensable para el MVP

| Orden | ID   | PBI / Feature                            |  SP |  TF | Prioridad | Sprint | Referente | Estado    |
| ----: | ---- | ---------------------------------------- | --: | --: | --------- | -----: | --------- | --------- |
|     1 | F-01 | Definir la ruta y sus usuarios           |   5 |   4 | Alta      |      1 | Álvaro    | Por hacer |
|     2 | F-21 | Probar la señal Wi-Fi                    |   5 |   2 | Alta      |      1 | Diego     | Por hacer |
|     3 | F-02 | Dividir la ruta y definir tiempos        |   8 |   7 | Alta      |      1 | Álvaro    | Por hacer |
|     4 | F-03 | Diseñar la conexión del sistema          |   5 |   3 | Alta      |      1 | Álvaro    | Por hacer |
|     5 | F-04 | Preparar el proyecto                     |   3 |   1 | Alta      |    1–2 | Álvaro    | Por hacer |
|     6 | F-05 | Guardar la información                   |   8 |   8 | Alta      |      2 | Álvaro    | Por hacer |
|     7 | F-06 | Crear el servidor y la API               |   8 |   7 | Alta      |      2 | Álvaro    | Por hacer |
|     8 | F-07 | Revisar y guardar eventos sin repetirlos |   8 |   8 | Alta      |      2 | Álvaro    | Por hacer |
|     9 | F-08 | Simular los puntos A, B y C              |   5 |   5 | Alta      |      2 | Diego     | Por hacer |
|    10 | F-09 | Mostrar la ruta, los nodos y los eventos |  13 |  10 | Alta      |      2 | Lucas     | Por hacer |
|    11 | F-10 | Controlar pasos pendientes entre puntos  |   8 |   8 | Alta      |      3 | Álvaro    | Por hacer |
|    12 | F-11 | Crear alertas por retraso                |   8 |   8 | Alta      |      3 | Álvaro    | Por hacer |
|    13 | F-12 | Atender y cerrar alertas                 |   8 |   8 | Alta      |      3 | Lucas     | Por hacer |
|    14 | F-13 | Mostrar el estado de los nodos           |   5 |   5 | Alta      |      3 | Diego     | Por hacer |
|    15 | F-14 | Iniciar sesión y controlar permisos      |   5 |   5 | Alta      |      3 | Álvaro    | Por hacer |
|    16 | F-15 | Contar entradas y salidas con un nodo    |  13 |   8 | Alta      |      4 | Diego     | Por hacer |
|    17 | F-16 | Enviar los datos por Wi-Fi               |   8 |   7 | Alta      |      4 | Diego     | Por hacer |
|    18 | F-19 | Agregar un segundo nodo                  |   8 |   5 | Alta      |      4 | Diego     | Por hacer |
|    19 | F-20 | Guardar y reenviar eventos               |   8 |   6 | Alta      |      4 | Diego     | Por hacer |
|    20 | F-22 | Mostrar estadísticas básicas             |   8 |   8 | Alta      |      5 | Lucas     | Por hacer |
|    21 | F-17 | Probar y medir el sistema                |  13 |   6 | Alta      |    3–5 | Valeria   | Por hacer |
|    22 | F-18 | Documentar y presentar el proyecto       |   8 |   3 | Alta      |      5 | Valeria   | Por hacer |

### Fuera del alcance actual — Won't for now

| ID   | Elemento excluido                               | Motivo                                               |
| ---- | ----------------------------------------------- | ---------------------------------------------------- |
| W-01 | Red para todo el Bosque La Primavera            | El MVP se limita a una ruta piloto.                  |
| W-02 | Detección automática de caídas                  | Requiere otros dispositivos y validación.            |
| W-03 | Identificación individual de visitantes         | El conteo será anónimo.                              |
| W-04 | Cámaras o reconocimiento facial                 | No son necesarios y elevan el riesgo de privacidad.  |
| W-05 | Detección de humo o incendios                   | Se eliminó del objetivo principal.                   |
| W-06 | Contacto automático con servicios de emergencia | Las alertas requieren validación humana.             |
| W-07 | Aplicación móvil y solicitud de SOS             | El MVP se concentra en sensores y dashboard.         |
| W-08 | Hardware certificado y operación permanente     | Corresponde a una fase posterior.                    |
| W-09 | Mapa geográfico                                 | La ruta A-B-C puede mostrarse sin mapa.              |
| W-10 | Actualización en tiempo real                    | Una actualización manual o periódica es suficiente.  |
| W-11 | Notificaciones externas                         | El operador vigilará el dashboard durante la prueba. |
| W-12 | Tercer nodo físico                              | Dos nodos bastan para validar una sección.           |
| W-13 | Puntuación de confianza de alertas              | Se mostrarán datos faltantes sin calcular un nivel.  |
| W-14 | Configuración desde el dashboard                | La ruta piloto se entregará preconfigurada.          |
| W-15 | Exportación de datos en CSV                     | Las estadísticas se consultarán en el dashboard.     |
| W-16 | Módulo de auditoría independiente               | La trazabilidad mínima se incluye en las alertas.    |

### Resumen de estimación por prioridad

| Prioridad          | Features | SP totales | TF totales |
| ------------------ | -------: | ---------: | ---------: |
| Alta               |       22 |        168 |        132 |
| **Total estimado** |   **22** |    **168** |    **132** |

## 3. Dependencias y preparación

### 3.1 Dependencias principales

| Feature | Depende principalmente de          | Motivo                                                            |
| ------- | ---------------------------------- | ----------------------------------------------------------------- |
| F-02    | F-01                               | La ruta debe conocerse antes de dividirla y definir tiempos       |
| F-21    | F-01                               | La cobertura se mide sobre puntos candidatos reales               |
| F-03    | F-01, F-21                         | La conexión debe responder a las condiciones de la ruta           |
| F-04    | F-03                               | La estructura del proyecto refleja la arquitectura aprobada       |
| F-05    | F-02, F-04                         | El modelo de datos utiliza rutas, secciones y contratos definidos |
| F-06    | F-04, F-05                         | La API necesita proyecto y esquema disponibles                    |
| F-07    | F-05, F-06                         | La validación e idempotencia ocurren al recibir eventos           |
| F-08    | F-03, F-06                         | El simulador necesita contratos y endpoints                       |
| F-09    | F-05, F-06                         | El dashboard necesita datos y API                                 |
| F-10    | F-02, F-07, F-08                   | Los pasos pendientes requieren tiempos y eventos válidos          |
| F-11    | F-10, F-13                         | Las alertas dependen de pasos pendientes y salud de nodos         |
| F-12    | F-11, F-14                         | La gestión requiere alertas y permisos                            |
| F-13    | F-06, F-08                         | El estado utiliza la API y mensajes `HEARTBEAT`                   |
| F-14    | F-05, F-06                         | Los roles deben conectarse con Supabase y Express                 |
| F-15    | F-03                               | El nodo físico implementa el contrato acordado                    |
| F-16    | F-07, F-15, F-21                   | El envío requiere nodo, autenticación y Wi-Fi viable              |
| F-19    | F-15, F-16                         | El segundo nodo reutiliza el diseño validado                      |
| F-20    | F-07, F-16                         | La cola debe conservar IDs y respetar idempotencia                |
| F-22    | F-05, F-09, F-11                   | Las estadísticas requieren datos, dashboard y alertas             |
| F-17    | Features entregadas en cada sprint | Las pruebas se ejecutan de manera incremental                     |
| F-18    | F-17 y flujo principal integrado   | La entrega documenta resultados comprobados                       |

### 3.2 Descomposición obligatoria de features grandes

Las features con 13 SP se conservarán como agrupadores, pero deberán dividirse
en tareas de máximo 8 SP antes de entrar a un sprint:

| Feature | Tareas mínimas sugeridas                                                                |
| ------- | --------------------------------------------------------------------------------------- |
| F-09    | Estructura del dashboard; vista de ruta y nodos; tabla de eventos e historial           |
| F-15    | Conexión GPIO; máquina de estados de dirección; filtros y eventos ambiguos              |
| F-17    | Pruebas de backend y algoritmo; sensores y Wi-Fi; dashboard, seguridad y flujo integral |

### 3.3 Definition of Ready

Una feature o tarea estará lista para entrar a un sprint cuando:

- tenga valor y alcance comprensibles;
- incluya criterios de aceptación verificables;
- tenga una persona responsable;
- sus dependencias estén terminadas o exista un plan explícito;
- estén disponibles componentes, accesos y ambiente de prueba;
- sus riesgos de seguridad hayan sido revisados;
- si supera 8 SP, haya sido dividida en tareas menores.

### 3.4 Definition of Done

Una feature o tarea estará terminada cuando:

- cumpla sus criterios de aceptación, incluidos casos de error;
- el código o documento esté versionado;
- haya sido revisada por otra persona del equipo;
- tenga pruebas y evidencia de ejecución;
- no contenga secretos ni datos personales reales;
- esté integrada con los módulos de los que depende;
- actualice la documentación relacionada;
- no tenga errores críticos conocidos;
- el Product Owner la revise cuando corresponda.

### 3.5 Atributos de cada Product Backlog Item

Cada PBI del backlog contiene o se relaciona con los siguientes atributos:

| Atributo                | Ubicación o uso                                        |
| ----------------------- | ------------------------------------------------------ |
| Identificador           | Código único `F-XX` en la tabla y descripción          |
| Título                  | Nombre breve de la funcionalidad                       |
| Historia de usuario     | Catálogo de la sección 4.1 en formato Como–quiero–para |
| Descripción             | Fichas detalladas de la sección 4                      |
| Orden                   | Posición relativa dentro de la prioridad               |
| Prioridad               | Alta, media, baja o fuera de alcance                   |
| Estimación de esfuerzo  | Story Points — SP                                      |
| Tamaño funcional        | TF simplificado                                        |
| Sprint candidato        | Sprint propuesto, sujeto a velocidad real              |
| Responsable             | Referente principal del PBI                            |
| Estado                  | Situación actual del trabajo                           |
| Dependencias            | Tabla de la sección 3.1                                |
| Criterios de aceptación | Condiciones verificables Dado–Cuando–Entonces          |

## 4. Historias de usuario y descripción de los PBIs

### 4.1 Catálogo de historias de usuario

| ID   | Historia de usuario                                                                                                                       |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| F-01 | Como Product Owner, quiero definir la ruta piloto y sus usuarios para asegurar que el prototipo responda a una necesidad real.            |
| F-02 | Como operador, quiero dividir la ruta en secciones con tiempos por dirección para interpretar correctamente los recorridos.               |
| F-03 | Como equipo de desarrollo, queremos definir contratos de comunicación para integrar nodos, backend y dashboard sin ambigüedades.          |
| F-04 | Como desarrollador, quiero disponer de proyectos base configurados para comenzar a trabajar de manera reproducible y segura.              |
| F-05 | Como administrador del sistema, quiero almacenar rutas, nodos, eventos y alertas relacionados para conservar información consistente.     |
| F-06 | Como consumidor del sistema, quiero una API uniforme para enviar y consultar información desde los distintos módulos.                     |
| F-07 | Como operador, quiero que sólo se acepten eventos válidos, autorizados y no duplicados para confiar en los conteos.                       |
| F-08 | Como equipo de desarrollo, queremos simular los puntos A, B y C para probar el sistema sin depender inicialmente del hardware.            |
| F-09 | Como operador, quiero visualizar la ruta, los nodos y los eventos recientes para conocer el estado general del sistema.                   |
| F-10 | Como operador, quiero conocer los pasos pendientes entre puntos para identificar secciones que requieren revisión.                        |
| F-11 | Como operador, quiero recibir advertencias y alertas cuando un paso exceda su tiempo para reaccionar oportunamente.                       |
| F-12 | Como operador, quiero reconocer, asignar y cerrar alertas para dar seguimiento a su atención.                                             |
| F-13 | Como operador, quiero conocer la salud y última comunicación de cada nodo para distinguir falta de datos de una posible anomalía.         |
| F-14 | Como administrador, quiero controlar el acceso mediante usuarios y roles para impedir acciones no autorizadas.                            |
| F-15 | Como operador, quiero que un nodo distinga entradas, salidas y cruces ambiguos para obtener conteos más confiables.                       |
| F-16 | Como operador, quiero que los eventos de las Raspberry lleguen por Wi-Fi a la plataforma para consultarlos oportunamente.                 |
| F-17 | Como Product Owner, quiero resultados de pruebas y métricas para evaluar si el prototipo cumple sus objetivos y conocer sus limitaciones. |
| F-18 | Como socio formador, quiero recibir documentación y una demostración para decidir si el concepto merece una fase posterior.               |
| F-19 | Como operador, quiero contar con un segundo nodo para monitorear físicamente una sección completa.                                        |
| F-20 | Como operador, quiero que los nodos guarden y reenvíen eventos después de una desconexión para evitar pérdida de información.             |
| F-21 | Como equipo de desarrollo, queremos medir la cobertura Wi-Fi en los puntos candidatos para confirmar que la comunicación es viable.       |
| F-22 | Como operador, quiero consultar estadísticas de cruces, tiempos y alertas para analizar el comportamiento de la ruta.                     |

Los PBIs F-03, F-04, F-08 y F-21 son **habilitadores técnicos**. Se expresan
desde la perspectiva del equipo porque no producen por sí solos una función
visible para el visitante, pero son necesarios para entregar y comprobar las
historias orientadas al usuario.

Las siguientes fichas contienen la descripción y los criterios de aceptación
detallados de cada PBI.

### F-01 — Definir la ruta y sus usuarios

Define con Manuel la ruta piloto, los usuarios reales, restricciones del lugar,
entradas, salidas, desvíos, permisos y procedimiento actual de atención.

**Aceptación:** **Dado** el levantamiento inicial, **cuando** Manuel lo revisa,
**entonces** quedan aprobados o señalados como pendientes la ruta, actores,
restricciones y protocolo.

### F-02 — Dividir la ruta y definir tiempos

Representa una ruta lineal con puntos A, B y C y secciones A-B y B-C. Cada
dirección tendrá tiempos esperado, de advertencia y crítico.

**Aceptación:** **Dada** la ruta validada, **cuando** se consulta el modelo,
**entonces** aparecen puntos y secciones ordenados, con identificadores y
tiempos documentados por dirección.

### F-03 — Diseñar la conexión del sistema

Define la comunicación entre nodos, backend, base de datos y dashboard,
incluidos los mensajes de eventos, `HEARTBEAT`, errores y alertas.

**Aceptación:** **Dado** cada mensaje, **cuando** se revisa su contrato,
**entonces** contiene identificador, campos, tipos, ejemplo y respuesta de
error.

### F-04 — Preparar el proyecto

Prepara la estructura para nodos, backend, Supabase, dashboard, simulador y
documentos, con instrucciones y variables de entorno de ejemplo.

**Aceptación:** **Dado** un entorno limpio, **cuando** se siguen las
instrucciones, **entonces** los proyectos base inician sin secretos reales en
el repositorio.

### F-05 — Guardar la información

Crea esquema, relaciones, restricciones, índices, políticas y datos de prueba
para rutas, puntos, secciones, nodos, eventos y alertas.

**Aceptación:** **Dada** una base vacía, **cuando** se aplican los archivos SQL,
**entonces** se crean las entidades, se carga la ruta A-B-C de prueba y las
políticas de acceso impiden operaciones no autorizadas.

### F-06 — Crear el servidor y la API

Implementa Express, conexión con Supabase, errores uniformes y endpoints para
salud, rutas, nodos, eventos, alertas y estadísticas.

**Aceptación:** **Dado** el backend configurado, **cuando** se consumen sus
endpoints, **entonces** responde con el formato acordado sin exponer secretos.

### F-07 — Revisar y guardar eventos sin repetirlos

Autentica nodos, valida mensajes y evita duplicar eventos reenviados con el
mismo `event_id`.

**Aceptación:** **Dado** un evento, **cuando** es válido y autorizado,
**entonces** se almacena una sola vez; si no lo es, se rechaza sin cambiar el
conteo. Un nodo desconocido, una clave incorrecta o un cuerpo inválido reciben
una respuesta de error y no modifican la base de datos.

### F-08 — Simular los puntos A, B y C

Genera eventos controlados por punto, dirección y hora para probar recorridos
normales, desfases, duplicados y desconexiones sin esperar al hardware.

**Aceptación:** **Dado** un escenario seleccionado, **cuando** se ejecuta,
**entonces** produce los eventos requeridos para verificar su resultado.

### F-09 — Mostrar la ruta, los nodos y los eventos

Presenta resumen operativo, ruta A-B-C, estados de nodos, eventos recientes e
historial mediante datos obtenidos de la API.

**Aceptación:** **Dados** eventos almacenados, **cuando** un usuario autorizado
abre el dashboard, **entonces** puede consultar ruta, nodos, eventos y última
actualización.

### F-10 — Controlar pasos pendientes entre puntos

El sistema registra cuando ocurre un cruce hacia una sección de la ruta. Cuando
se registra un cruce compatible en el siguiente punto, completa el paso
pendiente más antiguo. El sistema compara conteos y no identifica personas.

**Aceptación:** **Dado** un registro de salida del punto A hacia B, **cuando** se
registra una llegada al punto B, **entonces** el sistema completa el registro
pendiente más antiguo. Si no se registra la llegada, lo conserva como
pendiente. La regla se prueba también con varios pasos y recorridos en ambas
direcciones.

### F-11 — Crear alertas por retraso

Evalúa tiempos y genera estados `NORMAL`, `WARNING` y `CRITICAL`, identificando
la sección y dirección relacionadas.

**Aceptación:** **Dado** un paso pendiente, **cuando** supera los umbrales,
**entonces** cambia al nivel correspondiente sin crear alertas duplicadas. Si
el nodo de destino está desconectado, el sistema muestra información incompleta
y no presenta el caso como una alerta confiable de retraso.

### F-12 — Atender y cerrar alertas

Permite reconocer, asignar, investigar, resolver o descartar alertas y conserva
responsable, fechas, notas y cambios.

**Aceptación:** **Dada** una alerta, **cuando** un operador autorizado cambia su
estado, **entonces** se guardan el estado, usuario, hora y nota.

### F-13 — Mostrar el estado de los nodos

Procesa `HEARTBEAT`, batería y errores para mostrar estados `ONLINE`,
`DEGRADED`, `OFFLINE` o `MAINTENANCE` y señalar cuando faltan datos.

**Aceptación:** **Dado** un nodo activo, **cuando** deja de comunicar dentro del
tiempo permitido, **entonces** aparece desactualizado y después desconectado.
Cuando vuelve a enviar un `HEARTBEAT` válido, recupera su estado operativo.

### F-14 — Iniciar sesión y controlar permisos

Implementa inicio y cierre de sesión y permisos de Administrador, Operador y
Consulta mediante Supabase Auth.

**Aceptación:** **Dado** un usuario autenticado, **cuando** intenta una acción,
**entonces** se permite o rechaza según su rol y una acción rechazada no altera
los datos.

### F-15 — Contar entradas y salidas con un nodo

Construye un nodo con dos sensores para inferir dirección y filtrar cruces
rápidos, lentos, simultáneos o ambiguos.

**Aceptación:** **Dados** cruces controlados en ambos sentidos, **cuando** se
activan los sensores, **entonces** se genera un evento único con dirección o se
marca como ambiguo. El prototipo queda montado sin piezas sueltas ni cables que
interfieran con la prueba.

### F-16 — Enviar los datos por Wi-Fi

Envía desde la Raspberry eventos JSON autenticados hacia Express y verifica la
respuesta del servidor.

**Aceptación:** **Dado** un nodo conectado, **cuando** ocurre un cruce válido,
**entonces** llega a Express, se almacena y aparece en el dashboard. Un timeout
o una respuesta no exitosa se reportan al módulo de reintento sin perder el
evento.

### F-17 — Probar y medir el sistema

Incluye pruebas de lógica, sensores, comunicación, dashboard y seguridad, más
mediciones de precisión, pérdida, duplicados, alertas y latencia.

**Aceptación:** **Dado** el plan de pruebas, **cuando** se ejecuta, **entonces**
cada caso conserva evidencia y cada métrica se compara con su meta. El plan
incluye recorridos simultáneos, direcciones contrarias, nodo desconectado,
mensajes duplicados, pérdida de Wi-Fi y recuperación.

### F-18 — Documentar y presentar el proyecto

Prepara arquitectura, API, hardware, seguridad, pruebas, manual, resultados,
limitaciones y guion de demostración.

**Aceptación:** **Dado** el prototipo integrado, **cuando** se presenta,
**entonces** Manuel observa el flujo principal y registra retroalimentación.

### F-19 — Agregar un segundo nodo

Integra un nodo de destino para probar físicamente una sección completa.

**Aceptación:** **Dados** dos nodos, **cuando** se realiza un recorrido,
**entonces** ambos registran dirección y se compensa el paso pendiente.

### F-20 — Guardar y reenviar eventos

Conserva eventos no enviados y los reintenta con el mismo identificador cuando
regresa la conexión.

**Aceptación:** **Dado** un envío fallido, **cuando** vuelve la conexión,
**entonces** se entrega sin duplicarse y se elimina de la cola al confirmarse.

### F-21 — Probar la señal Wi-Fi

Mide alcance Wi-Fi, mensajes enviados y recibidos, pérdida y latencia en cada
punto de prueba.

**Aceptación:** **Dados** los puntos, **cuando** se realizan mediciones,
**entonces** quedan documentadas sus condiciones y resultados. Cada punto
seleccionado deberá alcanzar Express, recibir al menos 95 % de los mensajes de
prueba y registrar una latencia promedio no mayor a cinco segundos; si no
cumple, deberá reubicarse o declararse no viable.

### F-22 — Mostrar estadísticas básicas

Muestra cruces, tiempos, alertas, falsas alarmas y disponibilidad por filtros y
periodos dentro del dashboard.

**Aceptación:** **Dados** datos históricos, **cuando** se selecciona un periodo,
**entonces** las gráficas y totales corresponden con los registros almacenados.

## 5. Distribución prevista por sprint

| Sprint | Objetivo                         | Features candidatas                      | Resultado demostrable                                       |
| -----: | -------------------------------- | ---------------------------------------- | ----------------------------------------------------------- |
|      1 | Validar ruta, Wi-Fi y diseño     | F-01, F-21, F-02, F-03 y F-04            | Ruta viable, cobertura medida y arquitectura validada       |
|      2 | Construir el flujo simulado      | F-05 a F-09                              | Simulador → Express → Supabase → dashboard                  |
|      3 | Detectar y gestionar desfases    | F-10 a F-14 y pruebas de lógica de F-17  | Un desfase simulado produce y actualiza una alerta          |
|      4 | Integrar hardware y comunicación | F-15, F-16, F-19, F-20 y pruebas físicas | Dos nodos registran una sección y recuperan fallos de Wi-Fi |
|      5 | Medir, documentar y cerrar       | F-22, F-17 y F-18                        | Demostración extremo a extremo con métricas                 |

Las features de cada sprint son candidatas, no un compromiso automático. Al
terminar el Sprint 1, el equipo calculará su velocidad real y ajustará la carga
de los siguientes sprints. Cualquier función marcada fuera del alcance deberá
evaluarse y priorizarse como parte de una fase posterior.
