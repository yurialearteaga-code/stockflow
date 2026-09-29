# StockFlow --- Levantamiento de Requisitos

Versión: 1.0

Estado: Documento base para diseño y desarrollo.

1. Introducción

StockFlow es un sistema web de gestión, control y trazabilidad de
inventario, diseñado con enfoque multiempresa. Cada empresa deberá
mantener sus usuarios, productos, inventarios, movimientos, reportes y
configuraciones aislados de las demás.

Este documento formaliza los requisitos definidos para el proyecto y
servirá como base para los casos de uso, modelo de datos, arquitectura,
desarrollo y pruebas.

2. Objetivo

Definir los requisitos que deberá cumplir StockFlow para administrar
productos, lotes, ubicaciones, distribuidores, movimientos, ventas y
operaciones no comerciales, manteniendo trazabilidad de las acciones
realizadas.

3. Alcance

StockFlow contempla inicialmente:

Usuarios, roles y permisos.

Gestión independiente de empresas.

Productos.

Lotes y vencimientos.

Ubicaciones.

Distribuidores.

Movimientos de inventario.

Ventas.

Ferias y eventos.

Obsequios y consumo interno.

Devoluciones.

Inventarios físicos y ajustes.

Auditoría y trazabilidad.

Alertas.

Dashboard y reportes.

Exportación a Excel y PDF.

Seguridad y respaldos.

4. Requisitos funcionales

RF-01 --- Gestión de usuarios

RF-01.1: Registrar usuarios.

RF-01.2: Permitir inicio de sesión.

RF-01.3: Permitir recuperación de contraseña.

RF-01.4: Activar o inactivar cuentas.

RF-01.5: Asociar cada usuario con una empresa.

RF-01.6: Permitir múltiples roles por usuario dentro de una
empresa.

RF-01.7: Asociar las operaciones con el usuario que las ejecutó.

RF-01.8: Modificar datos administrativos según permisos.

RF-01.9: Proteger las contraseñas mediante mecanismos adecuados.

RF-01.10: Permitir exclusivamente al Administrador gestionar las
cuentas de usuarios.

RF-02 --- Roles y permisos

RF-02.1: Asignar uno o varios roles a un usuario.

RF-02.2: Permitir múltiples roles simultáneos.

RF-02.3: Controlar funcionalidades según roles y permisos.

RF-02.4: Impedir operaciones no autorizadas.

Roles iniciales considerados: Administrador, Responsable de Inventario,
Gerencia y Contabilidad. La matriz detallada de permisos se formalizará
durante los casos de uso.

RF-03 --- Empresas y configuración

RF-03.1: Registrar empresas.

RF-03.2: Mantener configuración independiente por empresa.

RF-03.3: Aislar la información entre empresas.

RF-03.4: Administrar parámetros propios de cada empresa.

RF-03.5: Mantener independientes nombres, logotipos, usuarios,
productos y demás información.

RF-04 --- Productos

RF-04.1: Crear productos.

RF-04.2: Registrar nombre, código, presentación/peso, precio
base, código de barras y estado, según corresponda.

RF-04.3: Mantener el código del producto independiente del
código contable.

RF-04.4: Activar o inactivar productos.

RF-04.5: Conservar el historial de productos mediante
inactivación.

RF-04.6: Configurar si el producto maneja lotes.

RF-04.7: Configurar si el producto maneja vencimiento.

RF-05 --- Lotes y vencimientos

RF-05.1: Crear lotes asociados a productos.

RF-05.2: Identificar cada lote.

RF-05.3: Relacionar cada lote con un producto.

RF-05.4: Registrar información de producción o entrada.

RF-05.5: Registrar fecha de vencimiento cuando corresponda.

RF-05.6: Consultar movimientos asociados a un lote.

RF-05.7: Generar alertas para productos próximos a vencer.

RF-06 --- Ubicaciones

RF-06.1: Crear y administrar ubicaciones.

RF-06.2: Contemplar bodega, vitrina, distribuidor y
feria/evento, entre otras.

RF-06.3: Consultar inventario por ubicación.

RF-06.4: Manejar ubicaciones temporales para eventos.

RF-06.5: Mantener separada la ubicación física de la propiedad
del producto.

RF-07 --- Distribuidores

RF-07.1: Registrar distribuidores.

RF-07.2: Administrar su información.

RF-07.3: Consultar unidades que permanecen como propiedad de la
empresa y están con el distribuidor.

RF-07.4: Registrar entregas iniciales como traslado.

RF-07.5: Registrar como venta las unidades compradas por el
distribuidor.

RF-07.6: Registrar reportes de ventas del distribuidor sin
convertirlos automáticamente en ventas de la empresa.

RF-07.7: No controlar el precio de reventa del distribuidor.

RF-08 --- Movimientos de inventario

RF-08.1: Registrar movimientos.

RF-08.2: Contemplar producción/entrada, traslado, venta,
obsequio, consumo interno, devolución, ajuste y
corrección/anulación.

RF-08.3: Registrar fecha, producto, lote, cantidad, precio
cuando corresponda, origen, destino, ubicación, responsable y
observaciones.

RF-08.4: Actualizar existencias como consecuencia de los
movimientos.

RF-08.5: Disminuir origen y aumentar destino en los traslados.

RF-08.6: Mantener trazabilidad de cada movimiento.

RF-08.7: Corregir errores mediante operaciones trazables y no
eliminando directamente el historial.

RF-09 --- Ventas

RF-09.1: Registrar cada venta.

RF-09.2: Registrar fecha, producto, lote, cantidad, precio de
venta de la empresa, ubicación, responsable y descuento cuando
aplique.

RF-09.3: Conservar el precio efectivamente utilizado.

RF-09.4: Registrar ventas realizadas en ferias.

RF-09.5: Registrar ventas realizadas a distribuidores.

RF-09.6: Afectar el inventario correspondiente.

RF-09.7: No sustituir con StockFlow los procesos contables o de
facturación.

RF-10 --- Ferias y eventos

RF-10.1: Registrar ferias o eventos.

RF-10.2: Registrar el envío de inventario mediante traslado.

RF-10.3: Consultar inventario asignado al evento.

RF-10.4: Registrar ventas del evento.

RF-10.5: Registrar obsequios del evento.

RF-10.6: Registrar el retorno de sobrantes mediante devolución o
traslado, según corresponda.

RF-11 --- Obsequios y consumo interno

RF-11.1: Registrar obsequios.

RF-11.2: Registrar fecha, producto, lote, cantidad,
destinatario, responsable y motivo/observación.

RF-11.3: Registrar consumo interno.

RF-11.4: Registrar el motivo del consumo.

RF-11.5: Disminuir inventario sin registrar estas operaciones
como ventas.

RF-12 --- Inventarios físicos y ajustes

RF-12.1: Registrar conteos físicos.

RF-12.2: Comparar cantidad física contra cantidad registrada.

RF-12.3: Identificar diferencias.

RF-12.4: Consultar el historial antes de ajustar.

RF-12.5: Registrar ajustes autorizados con motivo y responsable.

RF-12.6: Mantener trazabilidad de los ajustes.

RF-13 --- Auditoría y trazabilidad

RF-13.1: Registrar acciones relevantes.

RF-13.2: Registrar usuario, fecha/hora, acción, registro
afectado y, cuando sea posible, valores anteriores y nuevos.

RF-13.3: Mantener el historial de operaciones.

RF-13.4: Conservar trazabilidad de anulaciones.

RF-13.5: Proteger la información de auditoría contra
modificaciones libres.

RF-13.6: No eliminar directamente el historial de transacciones.

RF-14 --- Alertas

RF-14.1: Generar alertas de vencimiento.

RF-14.2: Contemplar alertas a 60 y 30 días antes del
vencimiento.

RF-14.3: Generar alertas de bajo inventario.

RF-14.4: Permitir configurar mínimos de inventario.

RF-14.5: Permitir consultar alertas a usuarios autorizados.

RF-15 --- Dashboard y reportes

RF-15.1: Proporcionar dashboard.

RF-15.2: Consultar inventario por producto, lote y ubicación.

RF-15.3: Consultar movimientos por periodo, tipo, producto,
lote, ubicación y usuario, según permisos.

RF-15.4: Consultar ventas por periodo.

RF-15.5: Consultar información de distribuidores.

RF-15.6: Consultar información de ferias y eventos.

RF-15.7: Generar reportes de movimientos y ventas por periodo.

RF-15.8: Exportar información a Excel y PDF.

RF-15.9: Respetar permisos y aislamiento empresarial.

RF-16 --- Seguridad y respaldos

RF-16.1: Requerir autenticación.

RF-16.2: Verificar autorización antes de operaciones
restringidas.

RF-16.3: Garantizar aislamiento multiempresa también en backend
y base de datos.

RF-16.4: Proteger información sensible.

RF-16.5: Contemplar respaldos.

RF-16.6: Contemplar recuperación a partir de respaldos.

RF-16.7: Mantener consistencia entre movimientos e inventarios.

5. Requisitos no funcionales

RNF-01 Seguridad: proteger acceso, credenciales e información.

RNF-02 Privacidad y aislamiento: impedir acceso entre empresas.

RNF-03 Integridad: mantener consistencia de inventarios y
movimientos.

RNF-04 Trazabilidad: asociar operaciones con usuario, fecha y
hora.

RNF-05 Auditabilidad: conservar evidencia de cambios relevantes.

RNF-06 Disponibilidad: permitir acceso a usuarios autorizados
bajo las condiciones de operación definidas.

RNF-07 Rendimiento: responder adecuadamente a operaciones
habituales.

RNF-08 Escalabilidad: permitir incorporar empresas, productos,
ubicaciones y operaciones.

RNF-09 Usabilidad: facilitar las operaciones habituales.

RNF-10 Mantenibilidad: facilitar mantenimiento y evolución del
software.

RNF-11 Adaptabilidad: permitir nuevos productos, ubicaciones,
movimientos y motivos.

RNF-12 Respaldo y recuperación: mantener mecanismos de copia y
recuperación de información.

6. MVP

La primera versión funcional priorizará autenticación, usuarios, roles,
multiempresa, productos, lotes, vencimientos, ubicaciones,
distribuidores, movimientos, ventas, ferias/eventos, obsequios, consumo
interno, devoluciones, inventarios físicos, ajustes, auditoría, alertas,
dashboard, reportes y exportación.

7. Fuera del alcance inicial

Contabilidad completa.

Facturación electrónica.

Nómina.

Gestión financiera integral.

Control del precio de reventa de distribuidores.

Cálculo contable avanzado de costos de transformación.

Integraciones contables complejas.

Aplicación móvil nativa.

Inteligencia artificial.

Campos personalizados avanzados.

8. Funcionalidades futuras

Integración con sistemas contables.

Gestión avanzada de costos.

Aplicación móvil.

Campos personalizados.

Notificaciones avanzadas.

Automatización.

Planes de licenciamiento.

Integraciones con otros sistemas empresariales.

9. Trazabilidad

Los requisitos deberán relacionarse posteriormente con las reglas de
negocio de docs/requirements/Reglas_negocio.md, los casos de uso, el
modelo de datos, la arquitectura, la implementación y las pruebas.

