# Estructura técnica integral del proyecto

## Sistema Inteligente de Monitoreo de Senderos para Apoyo al Rescate

| Dato                             | Definición                                              |
| -------------------------------- | ------------------------------------------------------- |
| Socio formador                   | Más Bosque Manu / nombre legal por confirmar con Manuel |
| Representante del socio formador | Manuel                                                  |
| Tipo de proyecto                 | Prototipo tecnológico académico                         |
| Duración de referencia           | 10 semanas                                              |
| Equipo de desarrollo             | Álvaro, Diego, Lucas y Valeria                          |
| Entorno inicial                  | Una ruta piloto del Bosque La Primavera                 |
| Presupuesto preliminar           | MXN 119,000 para el MVP completo de una ruta            |
| Versión del documento            | 1.0                                                     |
| Fecha                            | 1 de octubre de 2026                                    |

> **Naturaleza del sistema:** este proyecto será un prototipo de apoyo a la
> supervisión. Un desfase indica que una sección necesita revisión; no confirma
> por sí mismo que exista una persona accidentada. El sistema no sustituirá a
> Protección Civil, paramédicos, brigadistas ni sistemas profesionales de
> emergencia.

---

## 1. Resumen ejecutivo

El proyecto consiste en construir un prototipo que monitoree el paso de
visitantes por puntos fijos de una ruta. Cada punto registrará la hora y la
dirección de los cruces y enviará los eventos a un sistema central. El backend
comparará los eventos de puntos consecutivos y generará una advertencia cuando
existan pasos pendientes durante más tiempo del esperado.

Un dashboard web permitirá al administrador:

- visualizar la ruta y sus secciones;
- consultar conteos y tiempos de recorrido;
- conocer el estado de los dispositivos;
- recibir advertencias y alertas de desfase;
- reconocer, investigar, cerrar o descartar alertas;
- consultar estadísticas e historial;
- registrar notas sobre la atención realizada.

La aplicación móvil será un complemento. Permitirá que una persona consciente
solicite ayuda y comparta su ubicación cuando exista conectividad. No será el
mecanismo principal para detectar el caso de una persona inconsciente.

El prototipo inicial incluirá tres puntos de monitoreo —A, B y C— que formarán
dos secciones de prueba. Los sensores, el backend, la base de datos y el
dashboard se integrarán gradualmente. El sistema podrá demostrarse primero con
eventos simulados y después con nodos físicos.

---

## 2. Problema que se busca atender

Cuando una persona se accidenta en una zona sin señal y no puede pedir ayuda,
la notificación depende de que otra persona la encuentre o salga del bosque
para avisar. Esto puede retrasar la búsqueda y no proporciona una ubicación
precisa.

El proyecto no intenta detectar directamente una lesión. Busca responder una
pregunta más alcanzable:

> ¿En qué sección de una ruta existe un cruce pendiente que lleva más tiempo
> del esperado sin aparecer en el siguiente punto?

Esta información podría ayudar a delimitar una zona de revisión y reducir el
área inicial de búsqueda.

### 2.1 Ejemplo

```text
10:00  Punto A registra un ciclista hacia B
10:10  Tiempo esperado de llegada a B
10:15  El paso sigue pendiente: advertencia amarilla
10:20  El paso sigue pendiente: alerta roja de revisión
10:22  El administrador reconoce la alerta
10:27  Un brigadista inicia la revisión de la sección A-B
```

La alerta no deberá afirmar que el ciclista está accidentado. Podría haberse
detenido, regresado, salido por un camino no monitoreado o haber ocurrido un
error de sensor.

---

## 3. Objetivos

### 3.1 Objetivo general

Diseñar, construir e integrar un prototipo de monitoreo de una ruta que registre
cruces bidireccionales, detecte posibles desfases entre puntos consecutivos y
presente la información en una plataforma web para apoyar la revisión y las
labores de rescate.

### 3.2 Objetivos específicos

1. Modelar una ruta piloto con puntos y secciones identificables.
2. Construir al menos dos nodos físicos y simular un tercer punto cuando sea
   necesario.
3. Detectar la dirección de paso mediante dos sensores por punto.
4. Transmitir eventos directamente al backend mediante Wi-Fi.
5. Registrar eventos sin duplicarlos y conservar el historial.
6. Estimar tiempos normales de recorrido por sección y dirección.
7. Generar advertencias y alertas configurables por desfase.
8. Mostrar rutas, dispositivos, alertas y estadísticas en un dashboard web.
9. Permitir la gestión y trazabilidad de cada alerta.
10. Implementar una aplicación móvil complementaria para solicitudes manuales
    de auxilio.
11. Medir precisión, falsos positivos, latencia y pérdida de mensajes.
12. Documentar limitaciones y recomendaciones para una futura prueba piloto.

---

## 4. Alcance

### 4.1 Producto mínimo viable — MVP

El MVP deberá incluir:

- una ruta piloto lineal;
- tres puntos lógicos de monitoreo: A, B y C;
- dos secciones: A-B y B-C;
- dos sensores por punto para inferir dirección;
- envío de eventos desde nodos o simuladores;
- backend con API;
- base de datos;
- lógica de desfases;
- dashboard administrativo;
- estados de nodo conectado, desactualizado y desconectado;
- gestión del ciclo de vida de las alertas;
- historial y estadísticas básicas;
- autenticación de administrador;
- pruebas controladas y documentación.

### 4.2 Alcance complementario

Se realizará después de estabilizar el MVP:

- aplicación móvil con botón SOS;
- captura de coordenadas GPS;
- almacenamiento local y reintento del SOS;
- comunicación Wi-Fi entre los nodos y el backend;
- visualización geográfica sobre un mapa;
- notificación remota de prueba;
- exportación de registros a CSV.

### 4.3 Fuera del alcance inicial

- cubrir todo el Bosque La Primavera;
- identificar individualmente a cada visitante;
- reconocimiento facial o almacenamiento de imágenes;
- confirmar automáticamente que ocurrió un accidente;
- llamar automáticamente al 911;
- emitir alertas oficiales;
- garantizar cobertura inalámbrica total;
- garantizar operación permanente a la intemperie;
- instalar infraestructura sin autorización;
- detección de humo o incendios;
- detección automática de caídas;
- diagnóstico médico;
- seguimiento continuo por GPS de los visitantes;
- reemplazar procedimientos de rescate existentes.

---

## 5. Usuarios y actores

| Actor             | Necesidad principal                   | Interacción con el sistema               |
| ----------------- | ------------------------------------- | ---------------------------------------- |
| Administrador     | Supervisar ruta, nodos y alertas      | Utiliza el dashboard web                 |
| Brigadista        | Conocer sección y situación reportada | Consulta alertas y registra atención     |
| Visitante         | Solicitar ayuda cuando pueda hacerlo  | Utiliza la aplicación móvil opcional     |
| Nodo de monitoreo | Registrar cruces                      | Envía eventos por Wi-Fi a la API         |
| Product Owner     | Validar utilidad y requisitos         | Revisa incrementos, pruebas y resultados |

---

## 6. Supuestos necesarios para el prototipo

1. La ruta piloto será lineal o sus desvíos estarán claramente documentados.
2. Los puntos de monitoreo estarán ubicados donde el paso sea suficientemente
   estrecho.
3. La primera prueba se limitará preferentemente a ciclistas para evitar mezclar
   tiempos de senderistas y ciclistas.
4. Los cruces se realizarán de manera controlada durante la validación.
5. Cada punto físico de la prueba tendrá cobertura de una red Wi-Fi que permita
   alcanzar el backend.
6. Los dispositivos podrán utilizarse en laboratorio antes de una prueba de
   campo.
7. El socio formador validará la ruta, los tiempos y el protocolo de atención.
8. Las alertas serán revisadas por una persona antes de iniciar cualquier
   respuesta.

Si la ruta contiene salidas no monitoreadas, cruces, atajos o cambios de ruta,
la interpretación del desfase perderá confiabilidad. Estas condiciones deberán
mostrarse en el dashboard y en el reporte final.

---

## 7. Arquitectura general

```text
┌─────────────────── RUTA PILOTO ───────────────────┐
│                                                   │
│  Punto A          Punto B          Punto C         │
│  2 sensores       2 sensores       2 sensores      │
│  Raspberry +      Raspberry +      Raspberry +     │
│  Python + Wi-Fi   Python + Wi-Fi   Python + Wi-Fi  │
│       │                │                │           │
└───────┼────────────────┼────────────────┼───────────┘
        └────────────── Wi-Fi ────────────┘
                         │ HTTPS
                         ▼
                  ┌─────────────┐
                  │ Backend/API │◄──── Aplicación móvil
                  └──────┬──────┘      Solicitud SOS
                         │
                         ▼
                  ┌─────────────┐
                  │  Supabase   │
                  │ PostgreSQL  │
                  └──────┬──────┘
                         │
                         ▼
                  ┌─────────────┐
                  │ Dashboard   │
                  │    web      │
                  └─────────────┘
```

### 7.1 Arquitectura por capas

| Capa             | Responsabilidad                                                    |
| ---------------- | ------------------------------------------------------------------ |
| Sensores         | Detectar la interrupción de dos haces y determinar el orden        |
| Software de nodo | Leer GPIO, filtrar ruido, inferir dirección y crear eventos únicos |
| Comunicación     | Enviar los mensajes por Wi-Fi directamente al backend              |
| Backend          | Validar, almacenar, procesar reglas y generar alertas              |
| Base de datos    | Conservar rutas, eventos, nodos, alertas y auditoría               |
| Dashboard        | Mostrar información y permitir operaciones administrativas         |
| Aplicación móvil | Generar solicitudes manuales de auxilio                            |

### 7.2 Ubicación de cada componente

Durante el desarrollo y la demostración controlada, el backend Express y el
dashboard se ejecutarán en la Mac de un integrante. Las Raspberry de los puntos
se dedicarán a leer sensores y enviar eventos. Supabase permanecerá como
servicio externo para base de datos y autenticación.

| Equipo o servicio           | Software que ejecutará                                              |
| --------------------------- | ------------------------------------------------------------------- |
| Raspberry de punto A, B o C | Python para GPIO, dirección de paso, cola local y envío             |
| Mac del equipo              | Backend Node.js/Express y dashboard React durante desarrollo y demo |
| Supabase                    | Base de datos PostgreSQL y autenticación del administrador          |

En una implementación posterior, Express y el dashboard se publicarían en un
servidor con disponibilidad permanente. De esta manera el sistema no dependería
de que la Mac de un integrante permanezca encendida.

---

## 8. Módulo de sensores

### 8.1 Propuesta de hardware

| Componente            | Función                             | Opción inicial                                |
| --------------------- | ----------------------------------- | --------------------------------------------- |
| Computadora de nodo   | Ejecutar Python y procesar sensores | Raspberry Pi Zero 2 W o Raspberry disponible  |
| Sensores de paso      | Detectar secuencia y dirección      | Dos barreras infrarrojas por punto            |
| Interfaz GPIO         | Recibir las señales digitales       | Pines GPIO de la Raspberry Pi                 |
| Comunicación de campo | Enviar eventos al backend           | Wi-Fi integrado de la Raspberry Pi            |
| Indicadores           | Diagnóstico local                   | LED de estado y buzzer opcional               |
| Alimentación          | Energizar el nodo                   | Batería recargable; fuente USB en laboratorio |
| Protección            | Proteger componentes                | Caja de prototipo; protección exterior futura |

La selección definitiva dependerá de pruebas. También podrán evaluarse sensores
de tiempo de vuelo o radar si las barreras infrarrojas no ofrecen resultados
aceptables.

Cada Raspberry ejecutará un servicio en Python. Para leer sensores digitales se
podrá utilizar `gpiozero`; si el componente requiere otro protocolo, se usará la
biblioteca compatible con GPIO, I2C o SPI. El servicio deberá iniciar con el
sistema, registrar errores y recuperar su operación después de un reinicio.

### 8.2 Detección de dirección

Cada punto utilizará dos sensores separados físicamente:

```text
Secuencia S1 → S2 = dirección de entrada
Secuencia S2 → S1 = dirección de salida
```

El programa de Python del nodo deberá controlar:

- tiempo máximo entre activaciones;
- bloqueo temporal para evitar dobles conteos;
- interrupciones prolongadas;
- activación simultánea;
- evento ambiguo;
- reinicio del nodo;
- memoria temporal cuando no exista comunicación.

### 8.3 Estados del nodo

```text
BOOTING      Iniciando y validando componentes
ONLINE       Operación y comunicación normales
DEGRADED     Sensor o enlace con comportamiento anormal
OFFLINE      Sin comunicación dentro del tiempo permitido
MAINTENANCE  Fuera de servicio de forma planeada
```

### 8.4 Eventos producidos

- `PASSAGE`: cruce válido con dirección.
- `AMBIGUOUS_PASSAGE`: activación que no permite determinar dirección.
- `HEARTBEAT`: mensaje periódico de salud.
- `LOW_BATTERY`: batería inferior al umbral.
- `SENSOR_ERROR`: falla de lectura o autodiagnóstico.
- `BOOT`: reinicio del dispositivo.

---

## 9. Comunicación Wi-Fi

### 9.1 Estrategia

Cada Raspberry se conectará directamente a una red Wi-Fi y enviará los eventos
a la API de Express mediante peticiones HTTP o HTTPS. No se utilizará un
dispositivo intermediario ni otro enlace de comunicación.

```text
Raspberry nodo ──Wi-Fi/HTTP(S)──> API Express ──> Supabase
```

Durante el desarrollo, Express se ejecutará en la Mac del equipo y todos los
dispositivos estarán conectados a la misma red. En una implementación posterior,
Express podrá publicarse en un servidor y las Raspberry utilizarán HTTPS.

### 9.2 Responsabilidades de cada Raspberry

- conectarse a la red Wi-Fi configurada;
- leer los sensores y determinar la dirección;
- crear un identificador único para cada evento;
- convertir el evento a JSON;
- enviar el evento a Express;
- verificar la respuesta del backend;
- reintentar cuando falle la conexión;
- conservar localmente los mensajes pendientes;
- enviar periódicamente un `HEARTBEAT`;
- informar errores y batería baja cuando sea posible.

### 9.3 Mensaje enviado por la Raspberry

```json
{
  "event_id": "01J9Z8K2",
  "node_id": "node-a",
  "event_type": "PASSAGE",
  "direction": "IN",
  "occurred_at": "2026-10-01T10:00:00-06:00",
  "battery_percent": 82
}
```

La Raspberry enviará el mensaje mediante `requests.post()` de Python al endpoint
`POST /api/v1/device-events`, incluyendo una clave individual del dispositivo
en un encabezado HTTP.

### 9.4 Manejo de pérdida de comunicación

1. Cada evento tendrá un identificador único.
2. Si la petición falla, la Raspberry guardará el evento localmente.
3. El nodo reintentará con espera progresiva cuando recupere Wi-Fi.
4. El backend aceptará el reenvío pero no duplicará el registro.
5. El dashboard mostrará cuándo un dato llegó con retraso.
6. Si el nodo deja de mandar `HEARTBEAT`, cambiará a desactualizado y después a
   desconectado.

### 9.5 Limitación de cobertura

El sistema sólo podrá transmitir en tiempo real desde puntos con cobertura
Wi-Fi suficiente para alcanzar Express. Si un punto queda fuera de cobertura,
la Raspberry almacenará los eventos y los sincronizará posteriormente, pero el
administrador no recibirá una alerta inmediata. Antes de una prueba de campo se
deberán medir el alcance y la estabilidad de la red en cada punto.

---

## 10. Backend y API

### 10.1 Tecnologías recomendadas

| Elemento           | Tecnología                                  | Motivo                                                                |
| ------------------ | ------------------------------------------- | --------------------------------------------------------------------- |
| Lenguaje           | JavaScript sobre Node.js                    | Permite utilizar el mismo lenguaje en web, backend y aplicación móvil |
| Framework          | Express.js                                  | Creación de endpoints, middlewares y API REST                         |
| Validación         | Zod                                         | Validación de cuerpos, parámetros y respuestas                        |
| Base de datos      | Supabase Database — PostgreSQL administrado | Tablas relacionadas sin mantener un servidor propio de base de datos  |
| Acceso a datos     | `@supabase/supabase-js`                     | Cliente oficial para consultar y modificar Supabase desde JavaScript  |
| Autenticación      | Supabase Auth                               | Inicio de sesión y administración de sesiones                         |
| Cambios de esquema | Archivos SQL versionados                    | Creación reproducible de tablas, índices y políticas                  |
| Pruebas de API     | Bruno o Postman                             | Ejecutar y guardar casos HTTP sin introducir un framework adicional   |
| Pruebas de lógica  | `node:test`, cuando se necesiten            | Herramienta de pruebas incluida en Node.js                            |
| Documentación      | OpenAPI con Swagger UI                      | Contrato y prueba de endpoints                                        |

Express será el framework que exponga la API desde el backend. El dashboard y
la aplicación móvil consumirán esa API mediante `fetch` o Axios; Express no se
ejecutará dentro de las interfaces cliente.

El navegador utilizará Supabase Auth para iniciar sesión y enviará el token a
Express. El backend verificará la sesión y utilizará `supabase-js` para trabajar
con la base de datos. La clave secreta de servidor de Supabase existirá sólo en
el backend; nunca se incluirá en React, React Native, Raspberry ni Git.

### 10.2 Responsabilidades

- autenticar dispositivos y usuarios;
- validar tipos, campos, fechas y rangos;
- rechazar nodos desconocidos;
- evitar eventos duplicados por `event_id`;
- almacenar cruces, latidos y errores;
- actualizar `last_seen_at` de cada nodo;
- mantener balances por sección;
- evaluar reglas de tiempo;
- crear, escalar y cerrar alertas;
- proporcionar estadísticas;
- registrar las acciones de los administradores;
- recibir solicitudes SOS de la aplicación.

### 10.3 Endpoints iniciales

| Método  | Ruta                         | Uso                                     |
| ------- | ---------------------------- | --------------------------------------- |
| `POST`  | `/api/v1/device-events`      | Recibir eventos de las Raspberry        |
| `POST`  | `/api/v1/sos`                | Recibir solicitud manual de auxilio     |
| `POST`  | `/api/v1/auth/login`         | Iniciar sesión                          |
| `GET`   | `/api/v1/routes`             | Consultar rutas y secciones             |
| `GET`   | `/api/v1/nodes`              | Consultar nodos y estado                |
| `GET`   | `/api/v1/events`             | Consultar historial de eventos          |
| `GET`   | `/api/v1/alerts`             | Consultar alertas                       |
| `PATCH` | `/api/v1/alerts/:id`         | Reconocer, investigar o resolver alerta |
| `GET`   | `/api/v1/statistics/summary` | Obtener estadísticas generales          |
| `GET`   | `/api/v1/health`             | Verificar salud del backend             |

### 10.4 Respuestas y errores

La API utilizará respuestas consistentes:

```json
{
  "data": null,
  "error": {
    "code": "UNKNOWN_NODE",
    "message": "El nodo indicado no está registrado"
  }
}
```

No se deberán devolver contraseñas, claves de dispositivos, trazas internas ni
detalles sensibles.

---

## 11. Base de datos con Supabase

### 11.1 Tecnología

Se utilizará **Supabase**, que proporciona una base de datos PostgreSQL
administrada. Esto permite conservar el modelo relacional sin instalar ni
mantener PostgreSQL en las computadoras del equipo. Las tablas, restricciones,
índices y políticas se documentarán en archivos SQL dentro del repositorio.

Supabase también proporcionará el inicio de sesión de los administradores. El
dashboard utilizará la clave pública publicable únicamente para autenticación.
Las operaciones sensibles y la recepción de eventos pasarán por Express.

### 11.2 Entidades principales

#### `profiles`

- `id`, relacionado con el usuario de Supabase Auth
- `name`
- `role`
- `active`
- `created_at`

Las contraseñas y sesiones no se almacenarán en una tabla creada por el equipo;
serán administradas por Supabase Auth.

#### `routes`

- `id`
- `name`
- `description`
- `active`

#### `checkpoints`

- `id`
- `route_id`
- `code`
- `name`
- `latitude`
- `longitude`
- `order_index`

#### `segments`

- `id`
- `route_id`
- `start_checkpoint_id`
- `end_checkpoint_id`
- `expected_seconds`
- `warning_seconds`
- `critical_seconds`
- `active`

Los tiempos se configurarán por dirección. Si A→B y B→A tienen duraciones
diferentes, deberán existir reglas independientes.

#### `nodes`

- `id`
- `checkpoint_id`
- `device_key_hash`
- `software_version`
- `status`
- `battery_percent`
- `last_seen_at`

#### `passage_events`

- `id`
- `event_id` único
- `node_id`
- `checkpoint_id`
- `direction`
- `occurred_at`
- `received_at`
- `quality`
- `raw_payload`

#### `pending_passages`

- `id`
- `segment_id`
- `origin_event_id`
- `direction`
- `started_at`
- `matched_event_id`
- `matched_at`
- `status`

#### `alerts`

- `id`
- `type`
- `severity`
- `segment_id`
- `source_event_id`
- `status`
- `opened_at`
- `acknowledged_at`
- `resolved_at`
- `assigned_user_id`
- `resolution_type`
- `notes`

#### `sos_requests`

- `id`
- `request_id` único
- `latitude`
- `longitude`
- `accuracy_meters`
- `message`
- `occurred_at`
- `received_at`
- `status`

#### `audit_logs`

- `id`
- `user_id`
- `action`
- `entity_type`
- `entity_id`
- `created_at`
- `metadata`

---

## 12. Lógica de detección de desfases

### 12.1 Principio

El sistema no rastreará identidades. Mantendrá pasos pendientes por sección y
dirección. Cuando una persona cruce el siguiente punto, se cerrará el paso
pendiente más antiguo compatible. Esto será una aproximación FIFO, no una
correspondencia individual comprobada.

### 12.2 Ejemplo de balance

```text
Entradas de A hacia B:       5
Llegadas registradas en B:   4
Pasos pendientes:            1
```

### 12.3 Estados de un paso pendiente

```text
NORMAL      Dentro del tiempo esperado
WARNING     Superó el tiempo de advertencia
CRITICAL    Superó el tiempo crítico
MATCHED     Fue compensado por un cruce posterior
CANCELLED   Fue descartado por un administrador
```

### 12.4 Regla inicial

Para cada sección y dirección se configurarán:

- tiempo esperado;
- tiempo de advertencia;
- tiempo crítico.

Ejemplo inicial que deberá validarse:

| Trayecto | Esperado | Advertencia | Crítico |
| -------- | -------: | ----------: | ------: |
| A → B    |   10 min |      15 min |  20 min |
| B → A    |   14 min |      20 min |  28 min |
| B → C    |    8 min |      12 min |  16 min |
| C → B    |   11 min |      16 min |  22 min |

Estos valores no deberán elegirse arbitrariamente. Se calcularán con pruebas de
recorrido y se revisarán con el socio formador.

### 12.5 Pseudocódigo

```text
al recibir cruce en punto A hacia B:
    crear paso pendiente para la sección A-B
    iniciar temporizador lógico

al recibir cruce en punto B proveniente de A:
    buscar el paso pendiente compatible más antiguo
    si existe:
        marcarlo como MATCHED
        cerrar su advertencia o alerta activa
    si no existe:
        registrar cruce sin origen conocido

cada minuto:
    para cada paso pendiente:
        si nodo de destino está desconectado:
            marcar información como no confiable
            no afirmar que existe un desfase de visitante
        de lo contrario, si supera tiempo crítico:
            crear o escalar alerta CRITICAL
        de lo contrario, si supera advertencia:
            crear alerta WARNING
```

### 12.6 Factores de confianza

El dashboard podrá mostrar confianza baja, media o alta según:

- ambos nodos están en línea;
- no existen eventos ambiguos cercanos;
- no hubo pérdida de mensajes;
- la ruta no tiene una salida intermedia conocida;
- el conteo coincide antes del evento;
- el tiempo excede claramente el máximo configurado.

Una confianza alta seguirá sin equivaler a una confirmación de accidente.

---

## 13. Dashboard web

### 13.1 Tecnologías recomendadas

| Elemento        | Tecnología                                               |
| --------------- | -------------------------------------------------------- |
| Lenguaje        | JavaScript moderno — ES Modules                          |
| Framework       | React con Vite                                           |
| Estilos         | CSS Modules o Tailwind CSS, según experiencia del equipo |
| Consulta de API | Axios o `fetch` centralizado hacia la API de Express     |
| Gráficas        | Recharts                                                 |
| Mapa            | Leaflet con OpenStreetMap, si se utiliza mapa real       |
| Pruebas         | Lista de casos manuales; Vitest será opcional            |

Para el MVP se recomienda consultar el backend cada cinco segundos. La
actualización mediante Server-Sent Events o WebSocket será una mejora si queda
tiempo.

### 13.2 Pantallas

#### Inicio de sesión

- correo y contraseña;
- mensajes de error no sensibles;
- cierre de sesión;
- expiración de sesión.

#### Resumen operativo

- número de nodos activos;
- nodos desactualizados o desconectados;
- pasos pendientes;
- advertencias y alertas activas;
- solicitudes SOS;
- hora de última actualización.

#### Vista de ruta

```text
[A: EN LÍNEA] ── VERDE ── [B: EN LÍNEA] ── AMARILLO ── [C: EN LÍNEA]
```

Colores propuestos:

- verde: operación normal;
- amarillo: desfase en advertencia;
- rojo: desfase crítico o SOS;
- gris: información incompleta por nodo desconectado;
- azul: situación en investigación.

El color nunca será el único indicador; también se utilizarán texto e iconos.

#### Centro de alertas

Cada alerta mostrará:

- identificador;
- sección;
- dirección;
- hora del paso inicial;
- tiempo transcurrido;
- severidad;
- confianza estimada;
- estado de nodos relacionados;
- eventos relacionados;
- responsable de atención;
- notas e historial.

#### Gestión de alerta

```text
NUEVA → RECONOCIDA → EN INVESTIGACIÓN → RESUELTA
                                     └→ FALSA ALARMA
```

Las transiciones quedarán registradas en auditoría.

#### Nodos

- identificador y punto;
- estado;
- última comunicación;
- batería;
- versión del software del nodo;
- número de errores;
- opción de marcar mantenimiento.

#### Estadísticas

- cruces por hora y día;
- cruces por punto y dirección;
- tiempo promedio por sección;
- tiempo percentil 95 por sección;
- advertencias y alertas;
- falsas alarmas;
- disponibilidad de nodos;
- porcentaje de mensajes recibidos;
- eventos ambiguos.

#### Configuración

- tiempos por sección y dirección;
- periodo de `HEARTBEAT`;
- tiempo para considerar un nodo desactualizado;
- usuarios y roles;
- activación o desactivación de rutas y nodos.

---

## 14. Aplicación móvil complementaria

### 14.1 Tecnologías

- React Native;
- Expo para facilitar el prototipo;
- JavaScript moderno — ES Modules;
- Expo Location para coordenadas;
- almacenamiento local seguro o AsyncStorage para solicitudes pendientes;
- Axios o `fetch` para peticiones HTTPS a la API de Express.

### 14.2 Funciones del MVP móvil

- mostrar un botón grande de solicitud de ayuda;
- confirmar que el usuario desea enviar el SOS;
- obtener ubicación y exactitud disponible;
- enviar fecha, hora, coordenadas y mensaje opcional;
- mostrar si la solicitud fue recibida;
- almacenar una solicitud pendiente cuando no exista conexión;
- reintentar cuando regrese la conectividad;
- mostrar claramente que un mensaje pendiente todavía no fue recibido.

### 14.3 Limitación principal

El GPS puede obtener ubicación sin internet, pero la aplicación no puede
transmitir desde una zona completamente incomunicada. Por ello, la aplicación
es un canal complementario y no la solución principal para el caso de una
persona inconsciente.

---

## 15. Seguridad y privacidad

### 15.1 Principios

- recopilar la menor cantidad posible de datos;
- no identificar visitantes en el módulo de conteo;
- no utilizar cámaras en el MVP;
- no guardar contraseñas en texto plano;
- no subir secretos al repositorio;
- validar todos los mensajes;
- conservar trazabilidad de acciones administrativas;
- no convertir automáticamente una alerta en llamada oficial de emergencia.

### 15.2 Controles técnicos mínimos

| Riesgo                        | Control                                                          |
| ----------------------------- | ---------------------------------------------------------------- |
| Acceso no autorizado          | Supabase Auth, validación de sesión y roles                      |
| Dispositivo falso             | Clave individual por nodo y lista de dispositivos autorizados    |
| Manipulación en tránsito      | HTTPS entre Raspberry, app, dashboard y backend                  |
| Eventos duplicados            | Restricción única por `event_id`                                 |
| Datos inválidos               | Esquemas Zod en la API de Express y validación de rangos         |
| Fuerza bruta                  | Límites de intentos y registro de fallos                         |
| Secretos expuestos            | Variables de entorno y archivo `.env.example` sin valores reales |
| Acceso directo a tablas       | Row Level Security — RLS — en Supabase                           |
| Clave administrativa expuesta | Clave secreta de Supabase disponible únicamente en Express       |
| Cambios no trazables          | Tabla de auditoría                                               |
| Pérdida de datos              | Copia de seguridad durante pruebas y exportación final           |
| Nodo comprometido             | Revocación de la credencial del dispositivo                      |

### 15.3 Roles

| Rol           | Permisos                                                |
| ------------- | ------------------------------------------------------- |
| Administrador | Configurar rutas, nodos, usuarios y reglas              |
| Operador      | Consultar y gestionar alertas                           |
| Consulta      | Ver información sin modificarla                         |
| Dispositivo   | Enviar eventos; no consultar información administrativa |

### 15.4 Privacidad de la aplicación

Si se solicita nombre, teléfono o contacto de emergencia, deberá definirse:

- finalidad del dato;
- consentimiento;
- tiempo de conservación;
- quién puede consultarlo;
- procedimiento de eliminación.

Para el primer prototipo se recomienda que el SOS sea anónimo o utilice sólo un
identificador de prueba.

---

## 16. Tecnologías seleccionadas

| Área                             | Tecnología principal                      | Alternativa                                |
| -------------------------------- | ----------------------------------------- | ------------------------------------------ |
| Software de nodos                | Python 3                                  | —                                          |
| Acceso a sensores                | gpiozero y bibliotecas GPIO/I2C/SPI       | RPi.GPIO cuando sea necesario              |
| Gestión de dependencias de nodos | `venv` + `requirements.txt`               | Poetry si el equipo ya lo conoce           |
| Pruebas de nodos                 | Pytest                                    | `unittest` de Python                       |
| Computadora de nodo              | Raspberry Pi Zero 2 W                     | Raspberry Pi disponible para laboratorio   |
| Sensores                         | Barreras infrarrojas dobles               | ToF o radar                                |
| Comunicación                     | Wi-Fi con peticiones HTTP/HTTPS           | Red local para laboratorio                 |
| Backend                          | JavaScript + Node.js + Express            | —                                          |
| Validación                       | Zod                                       | Joi como alternativa                       |
| Persistencia                     | Supabase mediante `@supabase/supabase-js` | Consultas SQL controladas desde servidor   |
| Base de datos                    | Supabase Database — PostgreSQL            | —                                          |
| Autenticación                    | Supabase Auth                             | —                                          |
| Frontend                         | React + JavaScript + Vite                 | —                                          |
| Cliente HTTP web                 | Axios o `fetch`                           | —                                          |
| Gráficas                         | Recharts                                  | Chart.js                                   |
| Mapa                             | Leaflet + OpenStreetMap                   | Diagrama propio de ruta                    |
| Aplicación                       | React Native + Expo + JavaScript          | Aplicación web móvil                       |
| Pruebas backend                  | Bruno/Postman + `node:test` opcional      | Casos manuales documentados                |
| Pruebas frontend                 | Guion de pruebas manuales                 | Vitest opcional                            |
| Infraestructura                  | Proyecto alojado en Supabase              | Supabase local sólo si después se necesita |
| Control de versiones             | Git y GitHub/GitLab institucional         | Repositorio actual                         |
| Documentación API                | OpenAPI + Swagger UI para Express         | Colección de Bruno/Postman                 |

La elección deberá congelarse al terminar el sprint de arquitectura. Cambiar de
stack durante la integración sólo se permitirá si existe un bloqueo probado.

---

## 17. Estructura propuesta del repositorio

```text
Reto/
├── docs/
│   ├── arquitectura.md
│   ├── api.md
│   ├── hardware.md
│   ├── seguridad.md
│   ├── plan_pruebas.md
│   └── manual_operacion.md
├── edge/
│   ├── checkpoint-node/
│   │   ├── src/
│   │   │   ├── sensors.py
│   │   │   ├── direction.py
│   │   │   ├── transport.py
│   │   │   └── main.py
│   │   ├── tests/
│   │   └── requirements.txt
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── routes/
│   │   ├── schemas/
│   │   ├── services/
│   │   ├── app.js
│   │   └── server.js
│   └── tests/
├── supabase/
│   ├── schema.sql
│   ├── policies.sql
│   ├── seed.sql
│   └── README.md
├── dashboard/
│   ├── src/
│   │   ├── api/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   └── utils/
│   └── tests/
├── mobile/
│   ├── src/
│   └── tests/
├── simulator/
│   └── event-simulator/
├── infrastructure/
│   └── .env.example
└── README.md
```

No es necesario crear todas las carpetas desde el primer día. La estructura
deberá crecer conforme se aprueben los módulos.

---

## 18. Plan de desarrollo por sprints

### Sprint 1 — Validación y diseño

- confirmar nombre del socio formador;
- seleccionar una ruta y definir sus restricciones;
- validar actores y protocolo de atención;
- medir o simular tiempos por sección;
- crear arquitectura y contratos de mensajes;
- definir base de datos y API;
- seleccionar sensores y módulos de comunicación;
- crear wireframes del dashboard;
- aprobar backlog y criterios de aceptación.

**Resultado:** diseño validado y riesgos principales conocidos.

### Sprint 2 — Software base y simulador

- configurar repositorio y proyecto de Supabase;
- crear tablas, políticas, backend y conexión con Supabase;
- implementar recepción idempotente de eventos;
- crear simulador de puntos A, B y C;
- construir dashboard básico;
- mostrar nodos, eventos e historial.

**Resultado:** flujo simulador → backend → base de datos → dashboard.

### Sprint 3 — Reglas y alertas

- implementar secciones y tiempos configurables;
- crear pasos pendientes y correspondencia FIFO;
- implementar niveles `WARNING` y `CRITICAL`;
- agregar ciclo de vida y notas de alertas;
- agregar estado de nodos y `HEARTBEAT`;
- realizar pruebas automáticas.

**Resultado:** un desfase simulado produce y actualiza una alerta.

### Sprint 4 — Hardware y comunicación

- ensamblar dos nodos de conteo;
- calibrar dirección y filtros;
- conectar los nodos directamente con Express mediante Wi-Fi;
- medir estabilidad y alcance de la red;
- implementar reintentos y deduplicación;
- documentar alcance y pérdida de paquetes.

**Resultado:** un cruce físico aparece en el dashboard.

### Sprint 5 — Integración, móvil y cierre

- integrar tercer punto lógico o físico;
- agregar aplicación SOS si el núcleo está estable;
- ejecutar pruebas completas;
- corregir fallos prioritarios;
- medir métricas;
- preparar manual, demostración y reporte final;
- presentar limitaciones y siguiente fase.

**Resultado:** demostración extremo a extremo y evidencia documentada.

---

## 19. Distribución de responsabilidades

| Integrante     | Responsabilidad principal                 | Apoyo secundario                  |
| -------------- | ----------------------------------------- | --------------------------------- |
| Lucas          | Dashboard web y visualización             | Comunicación técnica              |
| Diego          | IoT, sensores y Python de los nodos       | Modelo de datos de dispositivos   |
| Valeria        | Aplicación móvil y documentación          | Pruebas de experiencia de usuario |
| Álvaro         | Backend, API y seguridad                  | Documentación e integración       |
| Todo el equipo | Pruebas, revisión de código e integración | Demostración final                |

Reglas de colaboración:

- toda tarea tendrá una persona responsable;
- cada cambio relevante será revisado por otra persona;
- los contratos de API y mensajes se acordarán antes de programar integraciones;
- ningún integrante deberá esperar al hardware para comenzar;
- los problemas se registrarán y priorizarán, no se ocultarán para la demo.

---

## 20. Backlog priorizado

### Must — indispensable

- modelar ruta, puntos y secciones;
- recibir eventos simulados;
- almacenar eventos sin duplicados;
- calcular pasos pendientes;
- generar advertencias y alertas;
- mostrar alertas y nodos en el dashboard;
- gestionar estados de alerta;
- autenticar administradores;
- simular nodo desconectado;
- integrar al menos un nodo físico;
- ejecutar y documentar pruebas.

### Should — importante

- dos nodos físicos;
- comunicación Wi-Fi desde los nodos;
- estadísticas y gráficas;
- exportación CSV;
- aplicación SOS;
- reintentos automáticos;
- registro de auditoría completo.

### Could — si queda tiempo

- mapa geográfico;
- actualización en tiempo real mediante SSE;
- notificación por correo o mensajería;
- tercer nodo físico;
- caja resistente para demostración;
- estimación de confianza;
- panel avanzado de configuración.

### Won't for now — no se hará en esta versión

- red para todo el bosque;
- detección de caídas;
- identificación de visitantes;
- cámaras;
- humo e incendios;
- contacto automático con servicios de emergencia;
- aplicación publicada en tiendas;
- hardware certificado.

---

## 21. Estrategia de pruebas

### 21.1 Pruebas unitarias

- validación de mensajes;
- eventos duplicados;
- cálculo de tiempos;
- transición de estados;
- creación y cierre de alertas;
- autenticación y permisos.

### 21.2 Pruebas de sensores

- cruce individual A→B;
- cruce individual B→A;
- persona detenida entre sensores;
- cruce rápido;
- cruce lento;
- dos personas juntas;
- activación simultánea;
- objeto o animal simulado;
- cien cruces repetidos;
- desconexión y reinicio.

### 21.3 Pruebas de comunicación

- recepción normal;
- mensaje perdido;
- mensaje duplicado;
- mensajes fuera de orden;
- nodo sin Wi-Fi o sin acceso al backend;
- recuperación de conexión;
- nodo fuera de alcance;
- batería baja;
- medición de latencia y alcance.

### 21.4 Pruebas del algoritmo

- llegada dentro del tiempo esperado;
- advertencia y posterior llegada;
- alerta crítica;
- regreso al punto de origen;
- varios pasos pendientes;
- nodo destino desconectado;
- salida no monitoreada simulada;
- cierre manual como falsa alarma.

### 21.5 Pruebas del dashboard

- permisos por rol;
- filtros;
- colores acompañados de texto;
- funcionamiento en computadora portátil;
- mensajes claros cuando no hay información;
- actualización de estados;
- historial y auditoría.

### 21.6 Pruebas de seguridad

- acceso sin sesión;
- usuario sin permiso;
- contraseña incorrecta;
- nodo desconocido;
- evento con campos inválidos;
- intento de duplicación;
- inyección de contenido en notas;
- ausencia de secretos en el repositorio.

Las pruebas de campo requerirán autorización y no deberán obstaculizar senderos,
poner cables peligrosos ni generar una falsa emergencia real.

---

## 22. Métricas de éxito

| Métrica                          |                                                 Meta del prototipo |
| -------------------------------- | -----------------------------------------------------------------: |
| Precisión de cruces individuales |                                      ≥ 95 % en pruebas controladas |
| Precisión de dirección           |                                     ≥ 95 % en pruebas individuales |
| Falsos cruces                    |                                   ≤ 5 % en el escenario controlado |
| Mensajes válidos recibidos       |                                   ≥ 95 % dentro del área de prueba |
| Eventos válidos almacenados      |                                             100 % de los recibidos |
| Duplicados contabilizados        |                                                                  0 |
| Alertas simuladas correctamente  |                                       100 % de los casos definidos |
| Eventos procesados visibles      |                                                              100 % |
| Latencia con conectividad        |                                              Promedio ≤ 5 segundos |
| Detección de nodo desactualizado |                                      Dentro del tiempo configurado |
| Falsas alertas                   | Medidas y documentadas; meta inicial ≤ 10 % en el guion controlado |
| Incidentes durante pruebas       |                                                                  0 |

Una métrica no alcanzada no deberá ocultarse. Se registrará el resultado, causa,
impacto y recomendación.

---

## 23. Presupuesto orientativo

El presupuesto se presenta en pesos mexicanos y corresponde a un MVP académico
para **una sola ruta, tres puntos lógicos y hasta tres nodos físicos**. Incluye
el valor económico del trabajo del equipo, aunque en el contexto universitario
los integrantes no reciban efectivamente ese pago.

El costo definitivo dependerá de cotizaciones, disponibilidad de Raspberry Pi,
componentes que ya tenga el equipo, características de la ruta y cobertura
Wi-Fi comprobada.

### 23.1 Supuestos de estimación

| Supuesto | Valor utilizado |
|---|---:|
| Duración total del MVP | 10 semanas |
| Integrantes | 4 desarrolladores |
| Dedicación promedio | 10 horas por persona por semana |
| Horas totales estimadas | 400 horas-persona |
| Tarifa académica de planeación | MXN 200 por hora |
| Ruta incluida | 1 ruta piloto |
| Puntos incluidos | A, B y C |
| Comunicación | Wi-Fi |

La tarifa de MXN 200 por hora es un valor interno para estimar el esfuerzo, no
una afirmación sobre el salario obligatorio o comercial de un desarrollador.
Una cotización profesional podría utilizar tarifas mayores e incluir impuestos,
prestaciones, soporte, administración y margen del proveedor.

### 23.2 Mano de obra del proyecto completo

| Integrante / área | Horas | Tarifa | Subtotal |
|---|---:|---:|---:|
| Álvaro — backend, API, seguridad e integración | 105 | MXN 200 | MXN 21,000 |
| Diego — Raspberry, sensores, Python y comunicación Wi-Fi | 115 | MXN 200 | MXN 23,000 |
| Lucas — dashboard web y visualización | 95 | MXN 200 | MXN 19,000 |
| Valeria — aplicación móvil, experiencia y documentación | 85 | MXN 200 | MXN 17,000 |
| **Total de desarrollo** | **400** | — | **MXN 80,000** |

Las horas incluyen planeación, programación, reuniones, integración, pruebas,
correcciones, documentación y preparación de la demostración.

### 23.3 Hardware, servicios y operación

| Concepto | Cantidad o periodo | Estimación |
|---|---:|---:|
| Raspberry Pi Zero 2 W o equivalente con microSD y fuente | 3 | MXN 6,000 |
| Sensores para conteo bidireccional | 6 | MXN 1,800 |
| Baterías, regulación y alimentación | 3 nodos | MXN 3,000 |
| Cajas, soportes y protección básica | 3 nodos | MXN 2,400 |
| Cableado, protoboards y consumibles | Lote | MXN 1,200 |
| Extensión o repetidor Wi-Fi para pruebas, si se requiere | 1 | MXN 2,500 |
| Traslados y pruebas de campo | Varias visitas | MXN 4,000 |
| Supabase y alojamiento temporal de Express | Hasta 3 meses | MXN 1,500 |
| Documentación, impresión y materiales de presentación | Lote | MXN 1,000 |
| **Subtotal sin mano de obra** | — | **MXN 23,400** |

Supabase y el alojamiento podrían costar MXN 0 durante el prototipo si los
planes gratuitos disponibles cubren las pruebas. Se conserva una reserva para
evitar que el presupuesto dependa completamente de esos planes.

### 23.4 Resumen del MVP completo de una ruta

| Categoría | Importe |
|---|---:|
| Mano de obra | MXN 80,000 |
| Hardware, servicios y operación | MXN 23,400 |
| Subtotal | MXN 103,400 |
| Contingencia del 15 % | MXN 15,510 |
| **Presupuesto total estimado** | **MXN 118,910** |
| **Total redondeado para planeación** | **MXN 119,000** |

El rango razonable de tolerancia para esta etapa es de aproximadamente **MXN
101,000 a MXN 137,000**, equivalente a una variación de ±15 %.

### 23.5 Presupuesto específico del Sprint 1

Para un Sprint 1 de dos semanas enfocado en validación, arquitectura, selección
de ruta, modelo de datos, wireframes y una prueba inicial de hardware:

| Concepto | Estimación |
|---|---:|
| 80 horas-persona × MXN 200 | MXN 16,000 |
| Visita inicial y traslados | MXN 2,000 |
| Una Raspberry de prueba con microSD y fuente | MXN 1,600 |
| Dos sensores y material inicial | MXN 700 |
| Servicios de desarrollo | MXN 0 |
| Subtotal | MXN 20,300 |
| Contingencia aproximada del 10 % | MXN 2,030 |
| **Total estimado del Sprint 1** | **MXN 22,330** |
| **Total redondeado del Sprint 1** | **MXN 22,500** |

Los componentes comprados durante el Sprint 1 forman parte del presupuesto del
MVP y no deberán cobrarse nuevamente al calcular el total acumulado.

### 23.6 Desembolso académico estimado

Si el trabajo del equipo no se paga y sólo se considera el dinero que
efectivamente debe desembolsarse, el costo del MVP sería aproximadamente:

| Concepto | Importe |
|---|---:|
| Hardware, servicios y operación | MXN 23,400 |
| Contingencia del 15 % | MXN 3,510 |
| **Desembolso aproximado** | **MXN 26,910** |

El tercer punto podrá simularse y la primera prueba podrá utilizar alimentación
USB para reducir el desembolso. No se comprarán todos los componentes antes de
demostrar el flujo con uno o dos nodos.

---

## 24. Riesgos y mitigaciones

| Riesgo                           | Consecuencia                      | Mitigación                                               |
| -------------------------------- | --------------------------------- | -------------------------------------------------------- |
| Dos personas cruzan juntas       | Conteo menor al real              | Punto estrecho, calibración y registro de limitación     |
| Animal u objeto activa sensor    | Falso cruce                       | Altura, filtros y pruebas                                |
| Dirección incorrecta             | Balance erróneo                   | Dos sensores, ventana temporal y eventos ambiguos        |
| Visitante se detiene             | Advertencia falsa                 | Tiempos con margen y validación humana                   |
| Visitante regresa                | Desfase incorrecto                | Detección bidireccional y reglas de compensación         |
| Salida no monitoreada            | Paso pendiente permanente         | Elegir ruta piloto lineal y documentar desvíos           |
| Nodo desconectado                | Falsa interpretación              | Estado gris; suspender conclusiones automáticas          |
| Pérdida o duplicación            | Estadísticas incorrectas          | IDs únicos, reintentos e idempotencia                    |
| Punto sin cobertura Wi-Fi        | El evento no llega en tiempo real | Medir cobertura, reubicar punto o ampliar la red         |
| Wi-Fi sin acceso a Express       | El nodo no puede enviar eventos   | Validar red y guardar eventos localmente para reintentar |
| Batería agotada                  | Nodo fuera de línea               | Telemetría y alerta de batería baja                      |
| Lluvia o polvo                   | Daño o lecturas erróneas          | Pruebas interiores; protección exterior posterior        |
| Robo o vandalismo                | Pérdida del nodo                  | Instalación autorizada y ubicación protegida             |
| Alcance excesivo                 | Proyecto incompleto               | Must/Should/Could y app sólo después del núcleo          |
| Datos personales expuestos       | Riesgo de privacidad              | Conteo anónimo y minimización de datos                   |
| Alerta interpretada como certeza | Respuesta inadecuada              | Lenguaje de “posible desfase” y validación humana        |

---

## 25. Despliegue y ambientes

### Desarrollo

- backend Express y dashboard React ejecutados en la Mac del equipo;
- base de datos y autenticación en un proyecto de Supabase;
- simulador local de eventos;
- datos ficticios;
- scripts SQL versionados;
- variables en `.env` no versionado.

La Mac escuchará en la red local, por ejemplo en
`http://192.168.1.50:3000`. Las Raspberry y la Mac deberán estar conectadas a la
misma red. La dirección concreta se configurará mediante una variable y no se
escribirá de forma fija en varios archivos.

### Pruebas integradas

- Mac del equipo como servidor de Express y React;
- nodos en laboratorio o espacio controlado;
- cobertura Wi-Fi para todos los puntos de prueba;
- respaldo de base de datos antes de cada demostración.

Flujo de la prueba:

```text
Raspberry con sensores ──Wi-Fi──> Express en la Mac ──internet──> Supabase
```

### Demostración

- entorno congelado y probado;
- usuario de demostración;
- guion con caso normal, advertencia, alerta y nodo desconectado;
- datos preparados sin alterar los resultados medidos;
- plan alterno con simulador si el Wi-Fi o hardware falla.

Publicar Express y React en un servidor será opcional durante el MVP, pero la
demostración sí necesitará internet para utilizar el proyecto de Supabase. Si
no existe conexión, deberá usarse un conjunto de datos local de contingencia o
posponerse la parte que depende de Supabase.

### Implementación real con internet

En una siguiente fase, Express y el dashboard deberán publicarse en un servidor
que permanezca activo:

```text
Raspberry nodo ──Wi-Fi/HTTPS──> Express publicado ──> Supabase
```

La Mac dejará de ser parte de la operación. Sólo se utilizará para desarrollo y
administración.

### Funcionamiento sin internet

Si una Raspberry pierde el Wi-Fi, no podrá comunicarse con Express ni con
Supabase. El nodo deberá conservar los eventos en un almacenamiento local —por
ejemplo SQLite o un archivo de cola— y sincronizarlos cuando recupere conexión.
Este mecanismo conserva el historial, pero no permite alertas inmediatas.

El almacenamiento local es una contingencia y no reemplaza la necesidad de un
canal de salida si se espera que un administrador ubicado fuera del bosque
reciba alertas inmediatamente.

---

## 26. Demostración final propuesta

1. Mostrar los puntos A, B y C en verde.
2. Realizar un cruce físico en A hacia B.
3. Mostrar el evento en el dashboard.
4. Simular el paso del tiempo hasta advertencia amarilla.
5. Simular que el desfase continúa hasta alerta roja.
6. Reconocer y asignar la alerta.
7. Registrar una nota de investigación.
8. Generar el cruce correspondiente en B y mostrar la compensación.
9. Resolver la alerta.
10. Desconectar un nodo y mostrarlo en gris, sin afirmar que existe accidente.
11. Enviar un SOS desde la aplicación, si el módulo fue completado.
12. Mostrar estadísticas, auditoría y resultados de pruebas.

---

## 27. Criterios de aceptación final

El proyecto se considerará completo cuando:

1. Exista una ruta con puntos, secciones y tiempos configurables.
2. Los eventos puedan generarse mediante simulador y al menos un nodo físico.
3. La dirección sea registrada en pruebas controladas.
4. El backend valide y almacene eventos sin duplicarlos.
5. Un paso pendiente genere una advertencia y una alerta.
6. Un nodo desconectado se distinga de un desfase real.
7. El dashboard muestre ruta, nodos, eventos, alertas e historial.
8. Un administrador pueda reconocer, investigar y resolver una alerta.
9. Existan autenticación, validación y auditoría básica.
10. Se ejecuten las pruebas acordadas y se conserven evidencias.
11. Las limitaciones se presenten de forma clara.
12. Manuel revise la demostración y emita retroalimentación.

---

## 28. Definición de terminado

Una tarea se considerará terminada cuando:

- cumpla criterios de aceptación verificables;
- tenga pruebas aplicables;
- haya sido revisada por otro integrante;
- no incluya secretos ni datos personales reales;
- esté integrada con la rama principal acordada;
- actualice la documentación relacionada;
- no tenga errores críticos conocidos;
- tenga evidencia de funcionamiento.

---

## 29. Decisiones pendientes para validar con el socio formador

1. Nombre correcto y legal de la asociación.
2. Ruta exacta para el escenario piloto.
3. Usuarios reales del dashboard.
4. Tiempo esperado entre los puntos de la ruta.
5. Existencia de desvíos o salidas intermedias.
6. Ubicación, alcance y estabilidad de los puntos Wi-Fi instalados.
7. Si la red permite peticiones HTTP/HTTPS desde cada Raspberry hacia Express.
8. Disponibilidad de energía en los puntos.
9. Protocolo actual cuando aparece una persona retrasada o accidentada.
10. Personas autorizadas para reconocer y cerrar alertas.
11. Información que realmente necesitan ver los brigadistas.
12. Permisos necesarios para una prueba física.
13. Si la aplicación móvil aporta suficiente valor para justificar su desarrollo.

---

## 30. Evolución posterior

Si el prototipo demuestra valor, una siguiente fase podría incluir:

- más rutas y puntos de acceso Wi-Fi;
- sensores exteriores más robustos;
- alimentación solar calculada;
- pruebas reales de cobertura;
- notificaciones a brigadistas autorizados;
- integración con procedimientos formales;
- clasificación separada de ciclistas y senderistas;
- modelos estadísticos de tiempo de recorrido;
- identificadores anónimos voluntarios para mejorar la correspondencia;
- dispositivos comerciales certificados.

Estas mejoras requerirán presupuesto, permisos, mantenimiento y validación
profesional. No deberán presentarse como parte ya resuelta por el prototipo.

---

## 31. Conclusión

La propuesta más viable para el equipo es construir un sistema de apoyo basado
en puntos fijos y un dashboard, no un sistema que pretenda confirmar accidentes.
El valor del proyecto estará en transformar cruces físicos en eventos
consultables, señalar desfases con contexto, diferenciar una anomalía de una
falla técnica y conservar trazabilidad de la atención.

El éxito no dependerá de instalar muchos dispositivos, sino de demostrar con
claridad y evidencia el siguiente flujo:

```text
Cruce físico → evento → comunicación → almacenamiento → regla → alerta → atención
```

Si este flujo funciona con una ruta pequeña, métricas conocidas y limitaciones
bien documentadas, el socio formador contará con información suficiente para
decidir si conviene realizar una prueba piloto de mayor escala.
