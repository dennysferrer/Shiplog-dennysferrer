# ShipLog — Plan del proyecto (borrador)

> **Estado:** especificación preliminar y preguntas de clarificación.
> **No es un plan aprobado.** Las decisiones de este documento quedan pendientes hasta recibir las respuestas a las preguntas de abajo.

---

## 1. Análisis de ShipLog

**Descripción del repo:** *"App para registrar los avances en proyectos independientes."*

ShipLog se entiende como un **registro de avances ("ship log") para proyectos independientes / personales**: un lugar donde una persona anota qué entregó, qué avanzó o qué aprendió en cada uno de sus proyectos, de forma que quede un historial cronológico consultable.

### Lo que se infiere
- **Usuario principal:** desarrollador/a o creador/a independiente (indie hacker, freelancer, persona con side projects).
- **Problema que resuelve:** los avances de proyectos personales se pierden entre commits, notas sueltas y redes sociales; falta una bitácora única y simple.
- **Unidad central:** la *entrada de avance* (log entry) asociada a un *proyecto*.
- **Valor:** constancia (ver progreso acumulado), memoria (qué se hizo y cuándo) y, potencialmente, visibilidad pública (compartir el progreso — "build in public").

### Lo que **no** está definido todavía
- Si es una herramienta solo personal o también social/pública.
- Qué datos tiene cada entrada (texto libre, etiquetas, enlaces, imágenes, métricas).
- Dónde se guardan los datos y cómo se autentica el usuario.
- Plataforma objetivo (web, móvil, CLI) y stack tecnológico.

---

## 2. Preguntas de clarificación

### 2.1 Alcance del producto
1. ¿ShipLog es **solo para uso personal** (un único usuario: tú) o **multiusuario** (cualquiera puede registrarse)?
2. ¿Plataforma objetivo: **web**, **móvil**, **CLI** o una combinación? ¿Cuál es la prioridad para el MVP?
3. ¿Qué tan importante es el aspecto **social / "build in public"** (perfiles públicos, feed, compartir) frente a ser una bitácora privada?
4. ¿Se necesitan **integraciones** en el MVP (p. ej. importar commits de GitHub, publicar en X/LinkedIn) o se deja para después?
5. ¿Hay algún **plazo** o hito concreto para el MVP?

### 2.2 Modelo de datos
1. ¿Qué campos debe tener un **proyecto**? (nombre, descripción, estado — activo/pausado/terminado —, enlace al repo/sitio, fecha de inicio…)
2. ¿Qué campos debe tener una **entrada de avance**? (título, cuerpo en markdown, fecha, etiquetas, enlaces, imágenes, tiempo dedicado…)
3. ¿Una entrada pertenece a **un solo proyecto** o puede asociarse a varios?
4. ¿Se requieren **etiquetas/categorías** (p. ej. `feature`, `bugfix`, `release`, `aprendizaje`)?
5. ¿Hace falta soportar **adjuntos** (imágenes, capturas) desde el MVP?
6. ¿Las entradas se pueden **editar/eliminar** después de creadas, o se busca un historial inmutable?

### 2.3 Visibilidad
1. ¿Los proyectos y entradas son **privados por defecto**, **públicos por defecto** o configurables por elemento?
2. ¿Debe existir una **página pública por usuario/proyecto** (URL compartible)?
3. ¿Se necesita un **feed** público o de seguidos, o basta con páginas individuales?
4. ¿Debe haber **interacción** (comentarios, reacciones) o solo lectura?

### 2.4 Stack de datos
1. ¿Preferencia de **base de datos / backend**? Opciones típicas:
   - BaaS: Supabase (Postgres), Firebase/Firestore.
   - Backend propio: Postgres/SQLite + API (Node/Next.js, Python, etc.).
   - Local-first: almacenamiento en el navegador o archivos markdown en el propio repo.
2. ¿Preferencia de **framework frontend** (Next.js, React + Vite, SvelteKit, otro)?
3. ¿Dónde se desplegaría (Vercel, Netlify, Fly.io, otro)? ¿Restricciones de costo (solo planes gratuitos)?
4. ¿Se necesita **exportar** los datos (markdown/JSON) desde el MVP?

### 2.5 Autenticación
1. ¿Se requiere **login** en el MVP? (Si es solo personal, podría bastar con un único usuario protegido.)
2. ¿Qué métodos: **email + contraseña**, **magic link**, **OAuth con GitHub/Google**?
3. ¿Se usará el proveedor de auth del BaaS elegido (p. ej. Supabase Auth, Firebase Auth) o uno dedicado (Auth.js, Clerk)?
4. ¿Hay requisitos de **roles** (admin, colaborador en un proyecto) o un único rol de usuario?

---

## 3. Nota sobre el estado del repositorio

- El repositorio `dennysferrer/Shiplog-dennysferrer` contiene únicamente el archivo `LICENSE` (MIT) y este documento.
- **No hay código de la aplicación** ni stack elegido todavía; este archivo es solo especificación y preguntas.
- El desarrollo comenzará una vez respondidas las preguntas de la sección 2 y aprobado el plan.

---

## 4. Propuesta preliminar de MVP (3 pantallas)

> **Pendiente de las respuestas del usuario.** Esta propuesta asume, de forma provisional, una app web multiusuario con login simple y proyectos privados por defecto con opción de hacerlos públicos. Puede cambiar por completo según las respuestas.

### Pantalla 1 — Mis proyectos (dashboard)
- Lista de proyectos del usuario con nombre, estado y fecha de la última entrada.
- Botón **"Nuevo proyecto"** (nombre, descripción, estado, enlace opcional).
- Indicador simple de actividad (p. ej. nº de entradas en los últimos 7/30 días).

### Pantalla 2 — Detalle de proyecto (timeline)
- Cabecera con datos del proyecto.
- **Línea de tiempo** cronológica de entradas de avance (más recientes primero).
- Filtro básico por etiqueta.
- Acceso a crear, editar o eliminar entradas.

### Pantalla 3 — Nueva / editar entrada
- Formulario: título, cuerpo en markdown con vista previa, fecha (por defecto hoy), etiquetas, enlaces.
- Selector de visibilidad (privada/pública) si se confirma esa funcionalidad.
- Guardar y volver al timeline del proyecto.

### Fuera del MVP (provisional)
- Feed social, comentarios y reacciones.
- Integraciones (GitHub, redes sociales).
- Adjuntos de imágenes y exportación de datos.

---

## 5. Próximos pasos

1. Responder las preguntas de la sección 2.
2. Ajustar el modelo de datos y la propuesta de MVP según las respuestas.
3. Aprobar el plan definitivo antes de escribir código.
