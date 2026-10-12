<div align="center">

# 🅿️ estacionando

### Informe completo del proyecto — tecnología, arquitectura y metodología ágil

**Capstone (PTY4614) · Ingeniería en Informática · DUOC UC, sede Antonio Varas**
Lorenzo Teixido · Martín Labra · Gaspar Díaz — docente guía Rocío Contreras Águila
Santiago de Chile, octubre de 2026

[![Next.js](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Java](https://img.shields.io/badge/Java-21-ED8B00?logo=openjdk&logoColor=white)](https://openjdk.org)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-4.1-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Supabase-336791?logo=postgresql&logoColor=white)](https://supabase.com)
[![Metodología](https://img.shields.io/badge/Metodología-Kanban-0A66C2)]()

**[🚀 App en vivo](https://estacionando.vercel.app)** · **[📡 Motores](https://estacionando.onrender.com/api/health)** · **[💻 Código](https://github.com/1loro/estacionando)**

</div>

> Este documento no reemplaza al `README.md` del repositorio — ese es la vitrina técnica para GitHub. Este es el informe completo: une el **qué se construyó**, el **cómo está hecho**, y el **cómo se gestionó** el trabajo, basado en el informe de metodología entregado a la asignatura.

---

## 1. Contexto general

**estacionando** es una plataforma digital de marketplace que conecta a conductores que necesitan encontrar un lugar para estacionar con anfitriones que disponen de espacios ociosos.

**Problema que aborda**
- Pérdida de tiempo durante la búsqueda de estacionamiento
- Congestión derivada de circulación innecesaria
- Espacios privados que permanecen ociosos durante parte del día

**Propuesta de valor**
- Publicación y administración de espacios por anfitriones
- Exploración de estacionamientos en lista y mapa
- Disponibilidad, horarios y tarifas como información central
- Flujo completo de reservas y gestión de reservas
- Evolución progresiva hacia pricing, ruteo, pagos, KYC y notificaciones según el roadmap

**Principio de transparencia del avance.** El proyecto adopta como regla que ninguna capacidad se presenta como terminada si no puede demostrarse de extremo a extremo. Este mismo criterio ordena el backlog, la Definition of Done, la presentación y este documento.

---

## 2. Metodología declarada y justificada

La metodología elegida es **Kanban adaptado al contexto académico**: un tablero visual de flujo continuo, con límites de trabajo en curso (WIP) y políticas explícitas para mover cada tarjeta entre columnas, sin iteraciones de duración fija.

### 2.1 Por qué Kanban

- Permite entregar valor de forma continua, sin esperar el cierre de un ciclo fijo
- Facilita incorporar observaciones docentes repriorizando el backlog apenas se reciben
- Prioriza funcionalidades según valor, dependencia y esfuerzo
- Exige revisar lo entregado en cada tarjeta, no solo la documentación
- Mantiene trazabilidad mediante Product Backlog, tablero, Definition of Done y retrospectivas
- Los límites WIP evitan abrir demasiados frentes a la vez

### 2.2 Roles

| Rol | Responsable | Función |
|---|---|---|
| Responsable de priorización | Equipo Estacionando | Prioriza el backlog según valor y feedback |
| Responsable de flujo | Rol rotativo | Vigila el tablero, límites WIP y bloqueos |
| Equipo de desarrollo | Integrantes | Desarrollo, documentación, pruebas y demo |
| Stakeholder | Docente / comisión | Evalúa y entrega feedback |

### 2.3 Flujo de trabajo

1. Priorizar ítems en la reunión de reposición
2. Mover las tarjetas a **Por hacer** respetando los límites WIP
3. Tomar tareas según capacidad disponible (sistema *pull*)
4. Desarrollar el ítem en la columna **En curso**
5. Validar con la Definition of Done antes de mover a **Hecho**
6. Preparar evidencia y demo
7. Recibir feedback
8. Retrospectiva y ajuste de backlog y políticas del tablero

> 🔧 **Esto no es solo un diagrama** — el tablero Kanban descrito en este informe está implementado y es funcional dentro de la propia app, en `/admin` → **Tareas Pendientes**: columnas Por hacer / En progreso / Hecho, con drag-and-drop y asignación de responsable por tarjeta, sincronizado en tiempo real entre administradores.

---

## 3. Product Vision

> Conectar conductores y anfitriones mediante una plataforma que facilite **publicar, encontrar, reservar y gestionar** estacionamientos.

### 3.1 Usuarios y necesidades

| Usuario | Necesidad principal | Valor esperado |
|---|---|---|
| Conductor | Encontrar y reservar estacionamiento | Menor fricción y mejor información para decidir |
| Anfitrión | Publicar y gestionar espacios | Monetizar capacidad ociosa y controlar disponibilidad |
| Administrador | Supervisar la operación | Control, trazabilidad y soporte |

### 3.2 Objetivos

**Objetivo general:** desarrollar una plataforma web funcional que conecte conductores y anfitriones mediante publicación, búsqueda y reserva de estacionamientos.

1. Gestionar cuentas
2. Publicar y administrar espacios
3. Explorar estacionamientos
4. Crear y gestionar reservas
5. Incorporar disponibilidad, precio y ubicación
6. Integrar progresivamente pricing y ruteo
7. Mantener un roadmap verificable

---

## 4. Product Backlog

Clasificado por prioridad (**Must / Should / Could**), dimensionado en Story Points, y con estado real al momento de este informe. Un ítem solo se considera **Hecho** cuando cumple la Definition of Done (sección 6).

| ID | Historia | Prioridad | SP | Estado |
|---|---|---|---|---|
| PB-01 | Registro de usuario | Must | 5 | ✅ Hecho |
| PB-02 | Inicio/cierre de sesión | Must | 3 | ✅ Hecho |
| PB-03 | Perfil y vehículos | Must | 5 | ✅ Hecho |
| PB-04 | Explorar espacios en lista/mapa | Must | 8 | ✅ Hecho |
| PB-05 | Ver detalle de estacionamiento | Must | 5 | ✅ Hecho |
| PB-06 | Publicar espacio | Must | 8 | ✅ Hecho |
| PB-07 | Editar/gestionar espacios | Must | 5 | ✅ Hecho |
| PB-08 | Crear reserva | Must | 8 | ✅ Hecho |
| PB-09 | Ver reservas | Must | 5 | ✅ Hecho |
| PB-10 | Cancelar reserva | Should | 5 | ✅ Hecho |
| PB-11 | Check-in/check-out | Should | 5 | 🔶 En curso |
| PB-12 | Evitar solapamiento de horarios | Must | 8 | 🔶 En curso |
| PB-13 | Mapa georreferenciado | Must | 5 | ✅ Hecho |
| PB-14 | Confirmar ubicación al publicar | Must | 5 | ✅ Hecho |
| PB-15 | Precio sugerido | Should | 8 | 🔶 En curso |
| PB-16 | Ruteo/recomendación | Should | 8 | 🔶 En curso |
| PB-17 | Dashboard administrador | Should | 8 | ✅ Hecho |
| PB-18 | Gestión admin avanzada | Should | 8 | 🔶 En curso |
| PB-19 | Incidencias | Should | 8 | 🔶 En curso |
| PB-20 | Reseñas | Could | 5 | 🔶 En curso |
| PB-21 | KYC real | Should | 13 | ⏳ Pendiente/parcial |
| PB-22 | Pagos reales | Must futuro | 13 | ⏳ Pendiente |
| PB-23 | Notificaciones | Should | 8 | ⏳ Pendiente |
| PB-24 | Pruebas automáticas | Must | 8 | ⏳ Pendiente |
| PB-25 | Seguridad/RLS | Must | 5 | 🔶 En curso |
| PB-26 | PWA/móvil | Could | 13 | ⏳ Pendiente |
| PB-27 | Observabilidad | Could | 8 | ⏳ Pendiente |
| PB-28 | Estados UX consistentes | Should | 5 | 🔶 En curso |

**Prioridad para los próximos ciclos de entrega:**
1. Cerrar publicación, disponibilidad y reserva
2. Asegurar persistencia y permisos
3. Integrar pricing y ruteo
4. Completar administración e incidencias
5. Integrar pagos y KYC
6. Agregar notificaciones, observabilidad y experiencia móvil

---

## 5. Tablero Kanban

El tablero registra **33 tarjetas: 1 en Hecho y 32 pendientes**, agrupadas por épica y vinculadas al ítem de backlog al que aportan. Cada tarjeta avanza solo cuando hay capacidad disponible según el límite WIP, y se cierra únicamente al cumplir la Definition of Done.

<details>
<summary><strong>Ver las 33 tarjetas (click para expandir)</strong></summary>

| ID | Tarjeta | Épica / ítem PB | Estado |
|---|---|---|---|
| KB-01 | Páginas de Términos y Privacidad | Legal | ✅ Hecho |
| KB-02 | Elegir proveedor (Webpay Plus/Transbank) + setup sandbox | Pagos (PB-22) | ⏳ Pendiente |
| KB-03 | Integración checkout: crear Payment en PENDING, redirigir | Pagos (PB-22) | ⏳ Pendiente |
| KB-04 | Route Handler de retorno/webhook que confirma el pago | Pagos (PB-22) | ⏳ Pendiente |
| KB-05 | Manejo de pago fallido / expirado | Pagos (PB-22) | ⏳ Pendiente |
| KB-06 | Reembolso automático (política 90/10) | Pagos (PB-22) | ⏳ Pendiente |
| KB-07 | Pruebas end-to-end contra el sandbox del proveedor | Pagos (PB-22) | ⏳ Pendiente |
| KB-08 | Decidir regla de negocio: verificación exigida solo al host | KYC (PB-21) | ⏳ Pendiente |
| KB-09 | Elegir proveedor (Didit / Truora / Metamap) + cuenta de prueba | KYC (PB-21) | ⏳ Pendiente |
| KB-10 | Flujo: botón "Verificar identidad" → widget del proveedor | KYC (PB-21) | ⏳ Pendiente |
| KB-11 | Route Handler que recibe el webhook y actualiza identity_verifications.status | KYC (PB-21) | ⏳ Pendiente |
| KB-12 | Gate en createParkingSpotAction/setSpotPublishedAction | KYC (PB-21) | ⏳ Pendiente |
| KB-13 | UI: badge "Anfitrión verificado" en perfil y tarjetas | KYC (PB-21) | ⏳ Pendiente |
| KB-14 | Admin: columna de estado de verificación en tabla de usuarios | KYC (PB-21) | ⏳ Pendiente |
| KB-15 | createReviewAction: 1 reseña por reserva/autor | Reseñas (PB-20) | ⏳ Pendiente |
| KB-16 | Regla: solo reseñar reservas cuyo endTime ya pasó | Reseñas (PB-20) | ⏳ Pendiente |
| KB-17 | Botón "Calificar" en historial de reservas | Reseñas (PB-20) | ⏳ Pendiente |
| KB-18 | Query de rating promedio + mostrarlo en perfil y tarjetas | Reseñas (PB-20) | ⏳ Pendiente |
| KB-19 | Admin: eliminar una reseña abusiva | Reseñas / Admin (PB-18) | ⏳ Pendiente |
| KB-20 | Elegir y configurar proveedor de email (Resend) | Notificaciones (PB-23) | ⏳ Pendiente |
| KB-21 | Plantillas de email: confirmada, cancelada, recordatorio | Notificaciones (PB-23) | ⏳ Pendiente |
| KB-22 | Crear filas en tabla notifications + disparar el email | Notificaciones (PB-23) | ⏳ Pendiente |
| KB-23 | UI: campanita de notificaciones con no leídas | Notificaciones (PB-23) | ⏳ Pendiente |
| KB-24 | Cron de recordatorio (Vercel Cron + route handler) | Notificaciones (PB-23) | ⏳ Pendiente |
| KB-25 | Modelo de token de reseteo + migración | Cuentas / Seguridad (PB-25) | ⏳ Pendiente |
| KB-26 | Flujo "Olvidé mi contraseña" completo | Cuentas / Seguridad (PB-25) | ⏳ Pendiente |
| KB-27 | Rate limiting básico en login/registro | Cuentas / Seguridad (PB-25) | ⏳ Pendiente |
| KB-28 | manifest.json + iconos + splash screen | PWA (PB-26) | ⏳ Pendiente |
| KB-29 | Service worker básico (shell offline) | PWA (PB-26) | ⏳ Pendiente |
| KB-30 | Prompt "Agregar a inicio" + meta tags | PWA (PB-26) | ⏳ Pendiente |
| KB-31 | Configurar Vitest/Jest para el lado Next.js | Calidad (PB-24) | ⏳ Pendiente |
| KB-32 | Tests: RUT, disponibilidad, condición de carrera | Calidad (PB-24) | ⏳ Pendiente |
| KB-33 | GitHub Action simple: build en cada push | Calidad (PB-24) | ⏳ Pendiente |

</details>

### 5.1 Criterios de cierre del ciclo de entrega

- Cada tarjeta cumple la Definition of Done antes de pasar a Hecho
- Pagos y verificación de identidad probados en sandbox, nunca presentados como integraciones productivas
- Build correcto en GitHub Actions en cada push
- Tests de lógica crítica (RUT, disponibilidad y reservas) pasando
- Emails y notificaciones verificados sobre reservas reales del entorno de prueba
- Informe y presentación consistentes con el estado real del tablero

---

## 6. Definition of Done

Estándar mínimo para declarar un ítem **Hecho** — evita que una pantalla, maqueta o implementación parcial se confunda con una funcionalidad terminada.

<table>
<tr><th>Categoría</th><th>Criterios</th></tr>
<tr><td><strong>Funcionalidad</strong></td><td>Cumple criterios de aceptación · funciona de principio a fin · incluye estados de error, carga y vacío · no depende de datos ficticios</td></tr>
<tr><td><strong>Código</strong></td><td>Versionado en Git · sin credenciales expuestas · build correcto · sin errores evidentes · se revisa cuando corresponde</td></tr>
<tr><td><strong>Datos y backend</strong></td><td>Lectura y escritura funcionan · validaciones implementadas · permisos revisados · cambios de base de datos documentados · errores controlados</td></tr>
<tr><td><strong>Experiencia de usuario</strong></td><td>Usable en escritorio y móvil · feedback al guardar/cancelar/publicar/reservar · errores comprensibles · previene acciones duplicadas · diseño consistente</td></tr>
<tr><td><strong>Integraciones</strong></td><td>Probadas en entorno real o de prueba verificable · variables de entorno documentadas · manejo de errores · un mock nunca se presenta como integración productiva</td></tr>
<tr><td><strong>Pruebas y evidencia</strong></td><td>Camino feliz probado · al menos un caso de error probado · evidencia disponible · presentación consistente con el estado real</td></tr>
</table>

> **Regla de calidad:** un elemento solo cambia a Hecho cuando existe evidencia verificable del comportamiento declarado.

---

## 7. Retrospectiva

### 7.1 Qué funcionó bien
Aplicación con varios flujos navegables · identidad visual clara · demo del problema y la solución · código y documentación técnica disponibles.

### 7.2 Qué no funcionó bien
Metodología insuficientemente documentada · faltaban Product Vision, backlogs, DoD y retrospectiva · BPMN con problemas de notación · la presentación mezclaba visión futura con estado actual · faltaba trazabilidad directa.

### 7.3 Causas identificadas
1. Se priorizó UI y funcionalidad sobre la evidencia metodológica
2. Los BPMN se construyeron como flujo lógico, no desde la semántica BPMN
3. No existía una DoD formal
4. La documentación estaba dispersa
5. No existía una matriz única de avance

### 7.4 Acciones de mejora

| Acción | Estado |
|---|---|
| Crear documentación metodológica | ✅ Hecho |
| Declarar Kanban adaptado | ✅ Hecho |
| Product Backlog y tablero Kanban | ✅ Hecho |
| Aplicar DoD | ✅ Hecho |
| Separar Hecho / En curso / Pendiente | ✅ Hecho |
| Corregir BPMN | ⏳ Pendiente |
| Resolver auditoría docente | ⏳ Pendiente del Excel |

### 7.5 Start / Stop / Continue

| Marco | Aplicación en Estacionando |
|---|---|
| **Start** | Trabajar con evidencias concretas, aplicar DoD, utilizar BPMN correcto y mantener trazabilidad |
| **Stop** | Sobredeclarar funcionalidades, usar conectores BPMN ambiguos, mantener documentación dispersa |
| **Continue** | Mantener identidad visual, demo funcional y refinamiento continuo a partir del feedback |

---

## 8. Stack tecnológico

| Capa | Tecnología | Para qué |
|---|---|---|
| Framework | Next.js 16 (App Router) · React 19 · TypeScript | Frontend y backend a la vez, vía Server Actions |
| Estilos | Tailwind CSS v4 · shadcn/ui · lucide-react | Sistema de diseño con tokens OKLCH, modo claro/oscuro |
| Datos | Prisma ORM · PostgreSQL | Esquema tipado, migraciones versionadas |
| Backend as a Service | Supabase (Postgres, Storage, Realtime) | Base de datos real, fotos, sincronización en vivo |
| Validación | Zod | Toda entrada se valida antes de tocar la base |
| Seguridad | bcryptjs · sesiones con hash SHA-256 | Contraseñas y tokens nunca se guardan en texto plano |
| Motores (servicio aparte) | Java 21 · Spring Boot 4.1 · Maven | Precio sugerido y optimización de ruta, vía REST |
| Mapas | Mapbox (Geocoding · Directions · Matrix) | Direcciones reales, rutas y tiempos de viaje |
| Infraestructura | Docker · GitHub (CI/CD por push) · Vercel · Render | Despliegue automático en cada push |

---

## 9. Avance del aplicativo y roadmap

Clasificación en tres estados — evita presentar interfaces o desarrollos parciales como capacidades completas.

**✅ Hecho / demostrable:** web responsive · registro y login · exploración · lista y mapa · detalle · publicación · fotografías · disponibilidad y tarifa base · mis espacios · perfil · reservas base · panel administrativo base · persistencia real con Supabase · páginas de Términos y Privacidad.

**🔶 En curso:** disponibilidad robusta · check-in/check-out · pricing dinámico integrado · ruteo integrado · administración avanzada · incidencias · reseñas · seguridad/RLS final.

**⏳ Pendiente:** pagos reales · KYC real · notificaciones · PWA/móvil final · observabilidad · hardening · pruebas de carga · analítica avanzada · recuperación de contraseña · pruebas automáticas y CI.

### 9.1 Roadmap propuesto

| Etapa | Objetivo | Alcance |
|---|---|---|
| Hito 1 | Consolidar MVP | Publicación, disponibilidad, reservas, permisos y pruebas |
| Hito 2 | Pricing + Ruteo | Precio sugerido, ranking/ruta y UX |
| Hito 3 | Confianza + Admin | KYC, incidencias, seguridad y panel |
| Hito 4 | Monetización | Pagos, estados, reembolsos y notificaciones |
| Hito 5 | Producto final | PWA/móvil, observabilidad, rendimiento y accesibilidad |

---

## 10. Matriz de trazabilidad y auditoría

| Requisito | Evidencia | Estado |
|---|---|---|
| Metodología declarada y justificada | Sección 2 | ✅ Completo |
| Product Vision | Sección 3 | ✅ Completo |
| Product Backlog | Sección 4 | ✅ Completo |
| Tablero Kanban | Sección 5 | ✅ Completo |
| Definition of Done | Sección 6 | ✅ Completo |
| Retrospectivas | Sección 7 | ✅ Completo |
| Avance del aplicativo | Sección 9 | ✅ Completo |
| Roadmap | Sección 9 | ✅ Completo |
| Auditoría docente | Matriz por observación | ⏳ Pendiente del Excel |
| BPMN corregidos | Bizagi / exportación | ⏳ Pendiente |

> **Regla de cierre de observaciones:** una observación solo se considera cerrada cuando existe evidencia verificable y el contenido responde directamente al comentario docente.

---

## 11. Fuentes y evidencias

- Repositorio académico Capstone-003D
- Repositorio de aplicación [estacionando](https://github.com/1loro/estacionando)
- Documentación técnica de estacionando (`diagrama-componentes.html`, `Documentacion-Tesis-Estacionando.docx`)
- Evidencias de fases anteriores
- Presentaciones y planillas existentes
- Tablero Kanban del proyecto, implementado en `/admin` → Tareas Pendientes (estado de tarjetas a octubre de 2026)

**Criterio de clasificación:**

| Estado | Criterio |
|---|---|
| Hecho | Demostrable y respaldado |
| En curso | Trabajo parcial o integración sin cierre total |
| Pendiente | Sin evidencia suficiente o definido como futuro |

---

## 12. Conclusiones

La documentación consolidada permite presentar estacionando con una base metodológica coherente y trazable. Kanban adaptado entrega una estructura clara para visualizar el flujo de trabajo, limitar el trabajo en curso, priorizar funcionalidades, definir qué significa "terminado", y convertir el feedback recibido en acciones concretas de mejora.

Los seis elementos solicitados por la docente —metodología declarada y justificada, Product Vision, Product Backlog, tablero Kanban, Definition of Done y retrospectivas— quedan identificados en secciones independientes y relacionados entre sí, junto con el estado real del aplicativo, un roadmap, la matriz de trazabilidad y las fuentes revisadas.

**El proyecto mantiene dos pendientes explícitos que no deben ocultarse:** la corrección final de los BPMN, y la revisión de la auditoría contenida en el archivo *"Resumen evidencias Antonio Varas.xlsx"*. Mantener estos puntos como pendientes es consistente con la propia Definition of Done y con la regla de no sobredeclarar funcionalidades o evidencias.

---

<div align="center">

**Lorenzo Teixido · Martín Labra · Gaspar Díaz** — DUOC UC, Capstone PTY4614

[![App en vivo](https://img.shields.io/badge/🚀_Probar_la_app-estacionando.vercel.app-3352DB?style=for-the-badge)](https://estacionando.vercel.app)

</div>
