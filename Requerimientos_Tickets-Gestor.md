# 🧩 1. FORMULARIO COMPLETO PARA CREAR UN TICKET

Aquí está el formulario estándar que debe llenar un cliente PARA crear un ticket.
Toda esta información será usada por el modelo de IA.

## FORMULARIO: Crear Ticket

### A. Datos del cliente (selección)

#### 1. Cliente (obligatorio)

**Tipo:** _Select_

**Opciones (10 clientes exactos del documento):**

- TechFin Solutions
- Retail Express
- LegalVerif y Corp
- Logística Rápida
- Recursos Humanos S.A.
- Marketing Cloud
- E-commerce Global
- HealthSecure
- Banco del Mañana
- Telecom Innova

_(Estas opciones vienen del documento oficial — tabla de clientes.)_

Cuando el usuario selecciona uno, el backend obtiene automáticamente:

  - MRR
  - Estado (Producción, Crítico, En riesgo de churn, etc.)
  - % usuarios afectados
  - Caso de uso principal
    
    (Sin mostrarlos en el formulario, pero sí usados en el cálculo.)

### B. Datos del ticket
#### 2. Título del ticket (obligatorio)

**Tipo:** Texto corto (_input_)

**Validación:** > 5 caracteres.

#### 3. Descripción del ticket (obligatorio)

**Tipo:** Textarea

**Validación:** > 20 caracteres.

#### 4. Tipo de ticket (obligatorio)

**Tipo:** _Select_

**Opciones:**

  - Incidente
  - Degradación del servicio
  - Caída total
  - Consulta / duda
  - Solicitud de cambio
  - Mejoras
  - Configuración
  - Facturación
    
    _(No viene en el documento, pero es estándar de soporte y requerido para mejorar clasificación → debe estar.)_

### C. Datos técnicos adicionales
#### 5. Entorno afectado (obligatorio)

**Tipo:** _Select_

**Opciones:**

- Producción
- Preproducción
- Integración
- QA

#### 6. % de usuarios afectados (opcional – override)

**Tipo:** _Select_

**Opciones:**

  - 0% (solo prueba del cliente)
  - 1–10%
  - 10–30%
  - 30–50%
  - 50–100%
    
    _(Si se deja vacío, se usa el dato oficial del cliente.)_



# 2. TODAS LAS PANTALLAS NECESARIAS (FRONTEND)

Lovable debe generar estas pantallas EXACTAMENTE:

## 📌 Pantalla 1 — Home / Dashboard

### Elementos:

- Botón `“Crear Ticket”`
- Tabla de “Histórico de Tickets”
- Contadores rápidos:
    - Tickets creados hoy
    - Tickets urgentes
    - Tickets corregidos vs confirmados

- Filtros:
    - Por cliente
    - Por prioridad
    - Por urgencia
    - Por estado (pendiente / confirmado / corregido)

### Tabla histórica debe mostrar:

- ID del ticket
- Cliente
- Título
- Prioridad asignada
- Urgencia
- SLA
- Estado feedback
- Fecha creación

## 📌 Pantalla 2 — Crear Ticket

- Formulario completo (sección anterior).
- Botón: “Enviar ticket”

## 📌 Pantalla 3 — Resultado de Clasificación IA

Después de enviar el ticket → mostrar tarjetas visuales.

### Bloque 1: Ticket Original

- Cliente
- Título
- Descripción

### Bloque 2: Resultado IA

- Prioridad (P1–P4) — con color:
    - P1 rojo
    - P2 naranja
    - P3 amarillo
    - P4 azul

- Urgencia (Crítica / Alta / Media / Baja)
- Impacto técnico (texto)
- Impacto negocio (texto)
- SLA asignado
- Categoría sugerida
- Nivel de confianza (%)
- Justificación (razonamiento del modelo)

### Bloque 3: Tickets similares (RAG)
Lista de 3–5 tickets del Knowledge_Base.json:
- Mostrar: ID, Título, Categoría, Prioridad, Urgencia

#### Botones de acción:
- “Confirmar clasificación”
- “Corregir clasificación” (abre modal)

## 📌 Modal: Corregir clasificación

Campos:

- Prioridad (_select_ P1–P4)
- Urgencia (_select_)
- SLA (auto por prioridad, editable)
- Categoría (_select_)
- Comentario del ingeniero

Al guardar:
  - Cambia el estado del ticket a “Corregido”
  - Visual indicador rojo/amarillo
  - Historial refleja la corrección
    
    (No requiere persistencia real.)

## 📌 Pantalla 4 — Ticket Detalle

Must have:

- Datos del ticket original
- Datos IA
- Datos de feedback
- Tickets similares
- Cliente e impacto
- Historial local de cambios

#  3. COMPORTAMIENTO DEL BACKEND (Lovable Internal + OpenAI)

Como elegiste:

- ✔ Backend de Lovable
- ✔ Motor IA = OpenAI
- ✔ RAG usando Knowledge_base.json (adjuntado)

Debemos definir EXACTAMENTE:

## A. Entradas que el backend enviará al modelo

Incluye:

1. Ticket nuevo
2. Datos del cliente
    -  MRR
    -  Estado (Producción / Crítico / En riesgo de churn)
    -  % usuarios afectados
    - Caso de uso
3. Matriz ANS (SLA)
4. Knowledge_base.json para similitudes
5. Tipo de ticket + entorno

## B. Proceso que debe ejecutar el backend

1. Recibe datos del formulario.
2. Enriquecer ticket con datos del cliente.
3. Buscar similitudes en Knowledge_base.json.
4. Llamar a OpenAI con contexto + datos.
5. Recibir respuesta con:
    - Prioridad
    - Urgencia
    - SLA
    - Categoría
    - Justificación
    - Impacto técnico
    - Impacto negocio
    - Nivel de confianza
    - Tickets similares
6. Guardar ticket en memoria interna (DB de Lovable).
7. Devolver respuesta al frontend.

## C. Criterios exactos de clasificación
### 1. Impacto técnico

Debe evaluar:
- Afectación total del servicio
- Caída del endpoint
- Error crítico (401/403/500/502/504)
- Performance grave (más de 8s, 30s, etc.)
- Integración caída
- Datos incorrectos/obsoletos
- Mensajería no responde
- Webhooks fallan
- Seguridad / autenticación

### 2. Impacto en el negocio

Según datos del cliente:

- MRR alto (>20k) → impacto mayor
- Estado “En riesgo de churn” → impacto mayor
- % usuarios afectados >50% → impacto crítico
- Caso de uso vital para operaciones → impacto P1/P2

### 3. Regla final para prioridad

| Caso                                 | Resultado |
|--------------------------------------|----------:|
| Caída total del servicio             |        P1 |
| Degradación severa (>50% usuarios)   |        P1 |
| Errores de autenticación o seguridad |        P1 |
| Integración externa crítica caída    |        P1 |
| Afectación alta pero no total        |        P2 |
| Problemas medianos de performance    |        P3 |
| Consultas / dudas / mejoras          |        P4 |

### 4. Urgencia

Ligada a prioridad pero independiente:

- Crítica = servicio caído / datos incorrectos / seguridad
- Alta = afecta flujo principal
- Media = afecta una parte menor
- Baja = no afecta operaciones

### 5. SLA (según documento ANS)

Asignación estricta según tabla:

| Impacto | Tiempo de Primera Respuesta  | Tiempo de Asistencia (Inicio de Trabajo) | Tiempo Objetivo de Solución |
|---------|-----------------------------:|-----------------------------------------:|----------------------------:|
| Crítico | 15 minutos                   | 30 minutos                               | 4 horas                     |
| Alto    | 30 minutos (Horario Laboral) | 1 hora (Horario Laboral)                 | 2 días hábiles              |
| Medio   | 1 hora (Horario Laboral)     | 4 horas (Horario Laboral)                | 5 días hábiles              |
| Bajo    | 4 horas (Horario Laboral) |  | 1 día hábil                              | 10 días hábiles             |

(El sistema devuelve estos valores.)


