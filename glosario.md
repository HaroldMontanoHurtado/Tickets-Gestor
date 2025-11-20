# GLOSARIO

Este será tu glosario definitivo para entender cada parte del reto.


------
### 🧠 1. Ticket

#### Definición técnica

Un ticket es un registro formal que representa un problema, solicitud, incidente o pregunta hecha por un cliente hacia un equipo de soporte.

#### Explicación simple

Es como cuando abres un “caso” o “reporte” para que soporte técnico te ayude. Cada reporte = 1 ticket.


#### Ejemplo

- “Los chats no se asignan a los agentes” → eso es un ticket.

#### En este proyecto

El sistema debe leer tickets en lenguaje natural y clasificarlos automáticamente.


------
### 🧠 2. Prioridad (P1, P2, P3, P4)

#### Definición técnica

La prioridad define qué tan urgente es atender un ticket basándose en el impacto en el negocio y la severidad del problema.

- P1 → Problema crítico. Debe atenderse de inmediato.
- P2 → Alto impacto, pero no caída total.
- P3 → Problema moderado o funcionalidad secundaria.
- P4 → Solicitudes o consultas sin urgencia.

#### Explicación simple

Es el “nivel de fuego”:

- P1 = incendio total
- P2 = mucho humo
- P3 = problema molesto
- P4 = no es urgente

#### En este proyecto

La IA debe seleccionar automáticamente la prioridad correcta para cada ticket según datos del cliente y del problema.


------
### 🧠 3. Urgencia (Crítica, Alta, Media, Baja)

#### Definición técnica

La urgencia indica qué tan rápido debe resolverse el ticket, considerando el tiempo que puede esperar el cliente.

#### Explicación simple

Es “qué tan rápido necesita una solución”.


#### Diferencia entre prioridad y urgencia

- **Prioridad:** impacto general → ¿qué tan grave es?
- **Urgencia:** tiempo → ¿con cuánta rapidez se debe resolver?

#### Ejemplo:

- Problema menor pero bloquea un proceso urgente → urgencia alta, prioridad media.


------
### 🧠 4. SLA (Service Level Agreement) / ANS

#### Definición técnica

Es un acuerdo formal de niveles de servicio: define tiempos máximos de respuesta, asistencia y resolución.

#### Explicación simple

Es el “tiempo límite” para trabajar el ticket.

#### Ejemplo:

- SLA: “Primera respuesta en 30 minutos, solución en 4 horas”.

#### En este proyecto

La IA debe estimar el SLA adecuado según el tipo de ticket.


------
### 🧠 5. Tiempo de Primera Respuesta
#### Definición técnica

Tiempo entre la creación del ticket y el primer contacto del equipo de soporte.

#### Explicación simple

“El tiempo que te tardas en decirle al cliente: ‘Ya vimos tu problema’.”


------
### 🧠 6. Tiempo de Asistencia

#### Definición técnica

Tiempo desde que se abre el ticket hasta que un ingeniero empieza a trabajar activamente en él.

#### Explicación simple

Es cuando el ingeniero deja de solo leer y realmente comienza a investigar.


------
### 🧠 7. Tiempo Objetivo de Solución

#### Definición técnica

Tiempo máximo en el que el ticket debe quedar resuelto (o con workaround).

#### Explicación simple

“El tiempo límite para entregar una solución, aunque sea temporal.”


------
### 🧠 8. Caso de uso

#### Definición técnica

Es el propósito principal para el cual un cliente usa la plataforma.

#### Explicación simple

Es “¿para qué usa el sistema este cliente?”

#### Ejemplo:

- “Validación de identidad”…
- “Chatbot de soporte”…

#### En este proyecto

Ayuda a la IA a entender el impacto real del problema.


------
### 🧠 9. MRR (Monthly Recurring Revenue)
#### Definición técnica

Ingreso mensual recurrente que el cliente paga por el servicio.

#### Explicación simple

Cuánto dinero representa ese cliente cada mes.

#### ¿Por qué importa?

Clientes con MRR alto suelen tener prioridad mayor.


------
### 🧠 10. RAG (Retrieval-Augmented Generation)
#### Definición técnica

Arquitectura donde un modelo de IA usa:

- Búsqueda semántica para recuperar información relevante (ej: tickets históricos).
- Generación para producir una respuesta final basada en esa información.

#### Explicación simple

Es como darle “la biblioteca correcta” al modelo antes de que responda.

#### Ejemplo real

Si un ticket nuevo habla de “Error 401 en WhatsApp”, el RAG busca tickets similares:

- T005: Error 401 → prioridad P1, urgencia crítica
- T008: fallas en WhatsApp → categoría CE-Disponibilidad

El modelo usa esos #### ejemplos para clasificar el ticket nuevo.

#### En este proyecto

El RAG es obligatorio para que la IA no invente respuestas y siga patrones reales.


------
### 🧠 11. Base de conocimiento (Knowledge Base)
#### Definición técnica

Es un repositorio de ejemplos, documentación, casos resueltos, guías, etc.

#### Explicación simple

Es la “memoria histórica” que alimentará el RAG.


------
### 🧠 12. Modelo de IA (OpenAI, Gemini, etc.)
#### Definición técnica

Es el motor de inteligencia artificial que interpreta el ticket y genera la clasificación.

#### Ejemplos:

- GPT-4.1
- Gemini 1.5
- Llama 3.1

#### En este proyecto

Puedes usar cualquier modelo que comprenda lenguaje natural.


------
### 🧠 13. Prompting
#### Definición técnica

Es la forma de “hablarle” a un modelo de IA para que dé la respuesta exacta que necesitas.

#### Explicación simple

El prompt es la “instrucción” que define cómo debe comportarse.

#### Ejemplo

- “Clasifica este ticket siguiendo los patrones recuperados por el RAG…”


------
### 🧠 14. Interfaz (Frontend)
#### Definición técnica

Es la parte visual con la que interactúa el usuario final.

Puede ser:

- web,
- móvil,
- herramienta low-code/no-code.

#### En este proyecto

Se usará para:

- crear tickets,
- mostrar clasificación automática,
- corregirla (feedback loop).


------
### 🧠 15. No-code / Low-code
#### Definición técnica

Plataformas que permiten crear aplicaciones sin escribir código o con código mínimo.

#### Ejemplos:

- Lovable
- Bubble
- Glide
- Retool

#### En este proyecto

Recomiendan Lovable para construir la UI rápidamente.


------
### 🧠 16. Feedback Loop
#### Definición técnica

Proceso donde el usuario revisa y corrige la respuesta automática de la IA, generando información para mejorar el sistema.

#### Explicación simple

Es cuando el ingeniero dice:

- “La IA acertó” → confirmar
- “La IA se equivocó” → corregir

#### En este proyecto

No necesitas guardar los cambios en una base de datos; solo mostrarlos visualmente.


------
### 🧠 17. Vector Database (vector DB)
#### Definición técnica

Base de datos optimizada para guardar vectores generados por modelos de IA, usados para búsquedas semánticas.

#### Ejemplos:

- Pinecone
- ChromaDB
- Weaviate
- Supabase Vector

#### Explicación simple

Es una base de datos donde cada texto se convierte en un “número gigante” y se compara con otros textos similares.

#### En este proyecto

Se usa en el componente RAG.


------
### 🧠 18. Embeddings
#### Definición técnica

Representación numérica (vector) de un texto, generada por IA, que contiene su significado.

#### Explicación simple

Es convertir un texto a un conjunto de números para que una computadora pueda entender su “significado”.

#### En este proyecto

Permite buscar tickets similares para el RAG.


------
### 🧠 19. Impacto
#### Definición técnica

Medida del daño o afectación que un incidente causa al cliente.

#### Explicación simple

¿Qué tan grave es para el negocio del cliente?

#### Ejemplo:

- “100% usuarios afectados” → impacto crítico.


------
### 🧠 20. Workaround
#### Definición técnica

Solución temporal mientras se arregla el problema de fondo.

#### Explicación simple

Un “parche” para que el cliente pueda seguir trabajando.


------
### 🧠 21. Integración
#### Definición técnica

Proceso donde un sistema se comunica con otro a través de API o conectores.

#### Explicación simple

Es cuando un módulo usa los datos o servicios de otro.

#### Ejemplo:

- Validación de identidad usando API de proveedor externo.


------
### 🧠 22. Integración externa
#### Definición técnica

Conexión con un servicio fuera de la empresa: API de WhatsApp, proveedor de antecedentes, etc.

#### Problema típico

- Si cambia algo del proveedor → tu sistema falla.


------
### 🧠 23. API
#### Definición técnica

Interfaz que permite que un sistema se comunique con otro mediante solicitudes estructuradas.

#### Explicación simple

Es “la puerta” por donde los sistemas hablan entre sí.

#### Ejemplo:

- /api/v2/identity/validate


------
### 🧠 24. Webhooks
#### Definición técnica

Mecanismo donde un servicio envía automáticamente una notificación HTTP hacia otro sistema cuando ocurre un evento.

#### Explicación simple

Es una “llamada automática” que el sistema hace cuando algo sucede.


------
### 🧠 25. Latencia
#### Definición técnica

Tiempo que tarda un sistema en responder. Tiempo entre enviar una solicitud y recibir respuesta, medido en milisegundos.

#### Explicación simple

Si se demora mucho → “lentitud”.

Tipos:

- latencia de red: velocidad del internet
- latencia de servidor: carga del backend
- latencia de aplicación: procesamiento interno


------
### 🧠 26. Balanceador de carga (Load Balancer)
#### Definición técnica

Módulo que reparte tráfico entre varios servidores para evitar sobrecarga.

#### Explicación simple

Un semáforo inteligente que decide qué servidor atiende cada solicitud.

#### Error típico

- Un loop mal configurado puede causar 502 Bad Gateway.


------
### 🧠 27. SDK (Software Development Kit)
#### Definición técnica

Conjunto de herramientas, librerías, documentación y utilidades que permiten integrar un servicio o funcionalidad en aplicaciones de terceros.

#### Explicación simple

Es un “paquete listo para usar” para conectar tu app con un servicio.

#### Ejemplo real

Un SDK de validación de identidad para Android ofrece:

- funciones para abrir la cámara,
- lectura de documento,
- validación de rostro,
- manejo de permisos.

#### En este proyecto

Algunos tickets mencionan problemas con SDK (Android 14, iOS), típicamente asociados a integraciones móviles.


------
### 🧠 28. MRZ (Machine Readable Zone)
#### Definición técnica

Zona de un pasaporte o documento con texto estructurado y legible por máquinas.

#### Explicación simple

La parte del pasaporte con letras y números en dos líneas que se pueden escanear automáticamente.

#### En este proyecto

Un ticket menciona soporte para MRZ europeo → esto implica actualizaciones de validación de documentos.


------
### 🧠 29. Backlog
#### Definición técnica

Cola de tareas o elementos pendientes por procesar.

#### Explicación simple

La “fila de cosas atrasadas”.

#### Ejemplo

- En mensajería WhatsApp, si se envían miles de mensajes, algunos pueden quedarse acumulados en backlog.


------
### 🧠 30. Cola (Queue)
#### Definición técnica

Sistema donde las solicitudes esperan en orden para ser procesadas.

#### Explicación simple

Es como una fila en un banco, pero de mensajes o tareas.

#### En este proyecto

Muchos problemas de campañas WhatsApp tienen que ver con colas saturadas.


------
### 🧠 31. Límite de simultaneidad
#### Definición técnica

Número máximo de tareas que un sistema puede ejecutar al mismo tiempo sin fallar.

#### Explicación simple

Cuántas cosas puede hacer un servicio simultáneamente antes de colapsar.


------
### 🧠 32. Encolación / Duplicación
#### Definición técnica

Errores donde un sistema mete múltiples veces la misma tarea en una cola.

#### Explicación simple

Como imprimir dos veces la misma factura porque diste doble click.


------
### 🧠 33. Token de autenticación
#### Definición técnica

Código temporal que permite a un sistema acceder a otro de forma segura.

#### Explicación simple

Es la “llave” para entrar a una API.

#### En este proyecto

Muchos tickets reportan fallas 401 / 403 por tokens vencidos o revocados.


------
### 🧠 34. Error 500 / 502 / 401 / 403 / 404

Son códigos HTTP que indican tipo de falla.

**500 → Error interno del servidor**
- El sistema tiene un problema interno.

**502 → Bad Gateway**
- Fallo en el intermediario (load balancer, proxy).

**401 → Unauthorized**
- Token inválido o no autorizado.

**403 → Forbidden**
- Tienes token, pero no tienes permiso.

**404 → Not Found**
- Recurso no existe.

#### Explicación simple

Son códigos numéricos que explican por qué algo falló.


------
### 🧠 35. Disponibilidad (Availability)
#### Definición técnica

Qué tan accesible y en funcionamiento está un sistema.

#### Ejemplo simple

- Caída total = disponibilidad 0%.


------
### 🧠 36. Performance
#### Definición técnica

Rendimiento del sistema: velocidad, consumo, uso de CPU.

#### Ejemplo

- Si una API tarda 30 segundos → performance degradada.


------
### 🧠 37. Calidad de datos
#### Definición técnica

Precisión, integridad y confiabilidad de la información procesada.

#### Ejemplo

- Datos desactualizados en antecedentes = mala calidad.


------
### 🧠 38. Verificación de antecedentes (Background Checks)
#### Definición técnica

Proceso de consultar bases de datos legales, penales o administrativas.

#### En este proyecto

Muchos tickets incluyen fallas del módulo de antecedentes.


------
### 🧠 39. Identidad digital / Validación de identidad
#### Definición técnica

Proceso de confirmar que una persona es quien dice ser.

Incluye:

- lectura de documento,
- reconocimiento facial,
- validación contra bases oficiales.


------
### 🧠 40. Onboarding
#### Definición técnica

Proceso inicial para registrar un usuario o cliente en una plataforma.

#### Ejemplo

- Tomar fotos, cargar documento, validar identidad.


------
### 🧠 41. Workflow / Flujo
#### Definición técnica

Secuencia de pasos automatizados que sigue un proceso.

#### Ejemplo

- Iniciar validación
- Subir documento
- Validar rostro
- Validar datos


------
### 🧠 42. Estado “pending”
#### Definición técnica

Estado intermedio donde un proceso está esperando respuesta o acción.

#### Explicación simple

Es como “cargando…” o “en proceso”.


------
### 🧠 43. Fallback
#### Definición técnica

Mecanismo alterno en caso de que el proceso principal falle.

#### Explicación simple

Un plan B automático.


------
### 🧠 44. Facturación (Billing)
#### Definición técnica

Sistema que cobra y genera facturas al cliente.

#### Ejemplo

- Cobra validaciones, campañas o antecedentes.


------
### 🧠 45. Internacionalización (i18n)
#### Definición técnica

Habilitar un sistema para múltiples idiomas/regiones.

#### Explicación simple

Convertir la aplicación para que funcione en otros países.


------
### 🧠 46. Exportación de datos
#### Definición técnica

Generar archivos (CSV, JSON, Excel) con datos históricos.


------
### 🧠 47. CSV
#### Definición técnica

Formato de texto plano separado por comas para almacenar tablas.

#### Ejemplo

- Una lista de clientes, tickets o validaciones exportada en excel → CSV.


------
### 🧠 48. Infraestructura
#### Definición técnica

Toda la capa técnica que soporta el sistema:

- servidores
- bases de datos
- load balancer
- contenedores
- redes
- microservicios


------
### 🧠 49. Microservicio
#### Definición técnica

Pequeño servicio independiente que cumple una función específica.

#### Ejemplo

- Un microservicio para imágenes en validación de identidad.


------
### 🧠 50. Error 504 (Gateway Timeout)
#### Definición técnica

La respuesta del servidor tardó demasiado y se agotó el tiempo.

#### Ejemplo simple

- “El servidor no respondió a tiempo.”


------
### 🧠 51. Cache
#### Definición técnica

Capa de almacenamiento temporal para acelerar consultas.

#### Ejemplo

- Datos de antecedentes desactualizados durante días = cache sin refrescar.


------
### 🧠 52. Index / Índice de base de datos
#### Definición técnica

Estructura que acelera búsquedas dentro de una base de datos.

#### Ejemplo

- Optimizar query para dashboard lento.


------
### 🧠 53. Demo

Demostración funcional solicitada por el cliente.


------
### 🧠 54. Contrato SLA

Documento formal que define tiempos de respuesta y penalizaciones.


------
### 🧠 55. Plataforma

La aplicación central que provee todos los módulos de servicio.



## 📊 GUÍA VISUAL COMPLETA

Aquí tienes un esquema visual que sintetiza todo el ecosistema:

~~~
                    ┌───────────────────────┐
                    │        CLIENTE        │
                    │   Radica un ticket    │
                    └───────────┬───────────┘
                                │
                                ▼
                ┌────────────────────────────────────┐
                │         FRONTEND (UI)              │
                │ ─ Formulario: título, descripción  │
                │ ─ Selección de cliente             │
                │ ─ Muestra clasificación IA         │
                │ ─ Feedback (confirmar/corregir)    │
                └───────────────┬────────────────────┘
                                │
                                ▼
            ┌────────────────────────────────────────────┐
            │ BACKEND SIMPLE / SERVERLESS                │
            │ Recupera datos del cliente (MRR, % afect.) │
            │ Envía info al motor IA                     │
            └───────────────────┬────────────────────────┘
                                │
                                ▼
            ┌──────────────────────────────────────────────┐
            │                  RAG                         │
            │ ─ Convierte ticket → embedding               │
            │ ─ Busca #### ejemplos similares en Vector DB │
            │ ─ Devuelve 5 tickets relevantes              │
            └───────────────────┬──────────────────────────┘
                                │
                                ▼
                ┌───────────────────────────────┐
                │        MODELO DE IA           │
                │ (OpenAI / Gemini / Llama...)  │
                │ ─ Clasifica prioridad         │
                │ ─ Clasifica urgencia          │
                │ ─ Calcula SLA                 │
                │ ─ Explica decisión            │
                │ ─ Devuelve nivel de confianza │
                └───────────────┬───────────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │ FRONTEND (RESULTADOS) │
                    │ ─ P1 / P2 / P3 / P4   │
                    │ ─ Crítica / Alta      │
                    │ ─ SLA                 │
                    │ ─ Explicación IA      │
                    │ ─ Feedback humano     │
                    └───────────────────────┘
~~~

