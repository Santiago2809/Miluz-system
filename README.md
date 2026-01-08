# Miluz Management System (MVP)

## 1. Contexto del negocio

Actualmente, la agencia de niñeras opera principalmente a través de WhatsApp como medio para coordinar servicios, comunicarse con niñeras y clientes, y llevar el control operativo del negocio. Aunque este enfoque ha funcionado hasta ahora, presenta varios problemas conforme el volumen de trabajo aumenta.

La información clave del negocio (servicios realizados, pagos, disponibilidad de niñeras, historial de clientes) se encuentra dispersa en múltiples conversaciones, lo que dificulta:
- Tener visibilidad clara de quién está trabajando y cuándo.
- Consultar rápidamente el historial de servicios de una niñera o cliente.
- Realizar cortes semanales de pagos sin revisar conversaciones pasadas.
- Detectar errores, omisiones o servicios no registrados.

La ausencia de un sistema centralizado genera dependencia del conocimiento manual de la administradora y aumenta el riesgo de errores operativos y financieros.

Este proyecto busca **sistematizar la operación interna** de la agencia sin cambiar radicalmente la forma en que se comunican con clientes y niñeras, utilizando un sistema administrativo que funcione como fuente única de verdad.

---

## 2. Objetivo del sistema

El objetivo principal del sistema es proporcionar una plataforma administrativa interna que permita a la agencia gestionar su operación diaria de manera clara, ordenada y confiable.

Los objetivos específicos del MVP son:
- Centralizar la información de niñeras, clientes y servicios.
- Tener visibilidad diaria y semanal de los servicios programados y realizados.
- Facilitar el control y cálculo de pagos semanales a niñeras.
- Reducir la dependencia de búsquedas manuales en conversaciones de WhatsApp.
- Mantener un historial consultable de servicios y pagos.

El sistema **no busca reemplazar WhatsApp como canal de comunicación**, sino complementar la operación con una herramienta estructurada para la gestión del negocio.

---

## 3. Alcance del MVP

### Incluye
- Gestión de niñeras (registro, edición y estatus).
- Gestión de clientes (información básica de contacto).
- Registro y seguimiento de servicios (eventuales, planta y nocturnos).
- Asignación de niñeras a servicios.
- Control de pagos semanales a niñeras.
- Registro de cobros a clientes.
- Visualización básica de servicios diarios y semanales.

### No incluye (en esta etapa)
- Portal para clientes.
- Portal para niñeras.
- Automatización de pagos bancarios.
- Integración con la API de WhatsApp.
- Sistema de calificaciones o reputación.
- Facturación electrónica.

Estas funcionalidades podrán considerarse en fases posteriores del proyecto.

---

## 4. Roles del sistema

El sistema contempla un uso interno con los siguientes roles:

### Admin
Rol principal, correspondiente a la dueña del negocio.
- Acceso total al sistema.
- Gestión completa de niñeras, clientes y servicios.
- Visualización y control de información financiera.
- Generación y cierre de cortes semanales de pagos.
- Configuración de tarifas base.

### Operadora
Rol de apoyo administrativo.
- Registro y edición de servicios.
- Asignación de niñeras a servicios.
- Consulta de información operativa.
- Sin acceso completo a reportes financieros globales.

La separación de roles busca mantener el control financiero centralizado sin limitar la operación diaria.
