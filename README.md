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

---

## 5. Flujo principal del negocio

El sistema está diseñado para reflejar el flujo operativo real de la agencia, desde que se solicita un servicio hasta que se realiza el pago a la niñera. El flujo principal (happy path) es el siguiente:

1. Un cliente solicita un servicio de niñera para una fecha y horario específicos.
2. La administradora u operadora registra el servicio en el sistema.
3. Se consulta la disponibilidad y el perfil de las niñeras para seleccionar una candidata.
4. Se asigna una niñera al servicio y se establece la tarifa correspondiente.
5. Se confirma el servicio con el cliente y la niñera a través de WhatsApp.
6. El servicio se lleva a cabo en la fecha y horario acordados.
7. Al finalizar el servicio, este se marca como completado en el sistema.
8. Al final de la semana, se genera un corte semanal de pagos.
9. Se realizan las transferencias a las niñeras y se registran como pagadas en el sistema.

Este flujo representa el escenario ideal. El sistema también contempla excepciones como cancelaciones, cambios de horario o sustitución de niñeras, las cuales se registran para mantener la trazabilidad operativa.

---

## 6. Entidades del sistema (modelo conceptual)

A continuación se describen las entidades principales del sistema a nivel conceptual. Esta sección define **qué representa cada entidad**, sin entrar aún en detalles técnicos o de implementación.

### Niñera
Representa a cada persona que presta servicios de cuidado infantil a través de la agencia.

Contiene información como:
- Datos personales básicos.
- Información de contacto.
- Zonas donde puede trabajar.
- Habilidades o características relevantes.
- Estatus operativo (activa, en pausa, etc.).
- Disponibilidad semanal de trabajo.

---

### Cliente
Representa a las madres, padres o tutores que solicitan servicios de niñera.

Contiene información como:
- Nombre.
- Teléfono de contacto.
- Dirección o zona.
- Notas relevantes para la atención del servicio.

---

### Servicio
Representa un turno o evento de trabajo en el que una niñera es asignada a un cliente.

Contiene información como:
- Cliente solicitante.
- Niñera asignada.
- Fecha y horario del servicio.
- Tipo de servicio (eventual, planta o nocturno).
- Tarifa aplicada.
- Estatus del servicio (solicitado, asignado, confirmado, completado, cancelado).
- Notas operativas.

El servicio es la entidad central del sistema, ya que conecta a niñeras, clientes y pagos.

---

### Disponibilidad
Representa los horarios en los que una niñera puede trabajar de forma recurrente.

Permite definir:
- Días de la semana disponibles.
- Rangos de horario por día.
- Múltiples bloques de disponibilidad por día.

La disponibilidad se utiliza como referencia para facilitar la asignación de servicios, pero no bloquea la operación de manera estricta.

---

### Pago a niñera
Representa el registro de pagos realizados a una niñera por los servicios prestados durante un periodo determinado.

Contiene información como:
- Periodo de pago (corte semanal).
- Monto total a pagar.
- Estatus del pago (pendiente, pagado).
- Fecha de pago.
- Referencia de la transferencia.

---

### Cobro a cliente
Representa el registro de los pagos realizados por los clientes a la agencia.

Contiene información como:
- Servicio asociado.
- Monto cobrado.
- Método de pago.
- Estatus del cobro (pendiente, pagado).

---

### Tarifas
Representa las tarifas base utilizadas por la agencia para calcular el costo de los servicios.

Contiene información como:
- Tipo de servicio.
- Tarifa por hora para el cliente.
- Tarifa por hora para la niñera.
- Reglas generales de aplicación.

Las tarifas pueden ser ajustadas manualmente por servicio en caso de excepciones.
