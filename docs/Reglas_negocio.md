# Reglas de Negocio — StockFlow

**Proyecto:** StockFlow  
**Versión:** 1.0  
**Empresa de referencia:** COMTUMAC  

---

## 1. Inventario y ubicaciones

### RB-001 — Inventario por ubicación

StockFlow debe controlar las cantidades de producto por ubicación, además de permitir consultar el inventario total de COMTUMAC.
Las ubicaciones pueden ser permanentes o temporales.

Ejemplos de ubicaciones:

- Bodega
- Vitrina
- Distribuidor
- Feria o evento
- Otras ubicaciones autorizadas

---

### RB-002 — Entrada de producción

Todo producto terminado producido ingresa inicialmente a Bodega.

El sistema debe quedar preparado para futuros escenarios en los que determinados lotes puedan tener un destino específico diferente.

---

### RB-003 — Movimientos de inventario

Todo movimiento que implique entrada, salida o cambio de ubicación debe quedar registrado en el sistema.

El inventario debe actualizarse automáticamente de acuerdo con el movimiento realizado.

---

## 2. Producción y lotes

### RB-004 — Registro de producción

Cada producción debe estar asociada como mínimo a:

- Fecha
- Lote
- Producto
- Cantidad de grano utilizada
- Cantidad producida
- Fecha de vencimiento
- Responsable
- Observaciones

La cantidad producida es la que ingresa al inventario.

La cantidad de grano utilizada debe conservarse para fines de trazabilidad y generación de reportes.

---

### RB-005 — Lotes

Los productos producidos deben estar asociados a un lote que permita identificar su origen y realizar seguimiento.

---

### RB-006 — Fecha de vencimiento

Cada lote debe conservar su fecha de vencimiento.

El sistema debe utilizar esta información para realizar seguimiento de los productos próximos a vencer.

---

## 3. Alertas de vencimiento

### RB-007 — Alertas preventivas

StockFlow debe generar notificaciones cuando un producto esté próximo a vencer.

La cantidad de días de anticipación debe ser configurable.

La alerta debe permitir identificar como mínimo:

- Producto
- Lote
- Cantidad disponible
- Ubicación
- Fecha de vencimiento

El sistema debe diferenciar entre productos vigentes, próximos a vencer y vencidos.

---

## 4. Distribuidores

### RB-008 — Producto en poder de distribuidores

Cuando COMTUMAC entrega producto a un distribuidor, las unidades continúan perteneciendo a COMTUMAC hasta que se realice el pago correspondiente.

El producto debe permanecer visible dentro del inventario controlado por COMTUMAC, asociado a la ubicación del distribuidor.

---

### RB-009 — Ventas reportadas por distribuidores

Los distribuidores pueden reportar las unidades que han vendido a sus clientes.

El sistema debe permitir conocer:

- Cantidad entregada al distribuidor
- Cantidad vendida/reportada
- Cantidad disponible en poder del distribuidor

Una venta reportada por un distribuidor no debe interpretarse automáticamente como un pago realizado a COMTUMAC.

---

## 5. Precios

### RB-010 — Precio de referencia

Cada producto puede tener un precio unitario de referencia.

El precio de referencia no representa necesariamente el precio final de cada venta.

---

### RB-011 — Precio real de venta

Cada venta debe conservar el precio unitario realmente aplicado en la operación.

El precio puede variar dependiendo de:

- Cantidad comprada
- Venta al por mayor
- Condiciones comerciales
- Feria o evento
- Otras condiciones autorizadas

Ejemplo:

Precio de referencia: $16.000

Venta normal: $16.000  
Venta mayorista: $15.000  
Venta mayorista: $14.000  
Venta en feria: $18.000

---

### RB-012 — Cálculo del total de una venta

El total de una venta debe calcularse mediante:

**Total = (Cantidad × Precio unitario) − Descuento**

---

## 6. Operaciones sin valor comercial

### RB-013 — Precio no aplicable

En las operaciones que no representan una venta, los campos económicos deben mostrar:

- Precio unitario: No aplica
- Descuento: No aplica
- Total: No aplica

Esto aplica inicialmente para:

- Producción
- Traslado
- Obsequio
- Consumo interno

---

## 7. Traslados

### RB-014 — Traslado de productos

Un traslado representa el cambio de ubicación física de un producto.

El traslado no representa una venta y no genera ingresos.

Ejemplo:

Bodega → Distribuidor

El sistema debe disminuir las unidades de la ubicación de origen y aumentar las mismas unidades en la ubicación de destino.

---

### RB-015 — Ubicación de origen y destino

Todo traslado debe registrar:

- Ubicación de origen
- Ubicación de destino
- Producto
- Lote
- Cantidad
- Fecha
- Responsable
- Observaciones

---

## 8. Devoluciones

### RB-016 — Movimiento de devolución

Una devolución representa la salida del producto de una ubicación y su posterior ingreso a otra ubicación.

Las unidades devueltas deben sumarse al inventario de la ubicación donde sean recibidas.

---

### RB-017 — Destino de una devolución

Una devolución no necesariamente debe regresar a Bodega.

Las unidades pueden ingresar a cualquier ubicación autorizada.

Ejemplos:

- Bodega
- Vitrina
- Otra ubicación autorizada

---

### RB-018 — Motivo de devolución

Las devoluciones deben permitir registrar un motivo.

El motivo conocido actualmente es:

- Reabastecimiento solicitado

El sistema debe quedar preparado para otros motivos futuros, como:

- Producto defectuoso
- Producto vencido
- Error en despacho
- Otro

---

## 9. Corrección y trazabilidad

### RB-019 — Modificación de movimientos

StockFlow debe permitir modificar información de un movimiento cuando sea necesario corregir datos.

---

### RB-020 — Anulación de movimientos

Los movimientos incorrectos no deben eliminarse físicamente.

El sistema debe permitir anular un movimiento para conservar el historial y la trazabilidad de las operaciones.

---

## 10. Obsequios

### RB-021 — Registro de obsequios

Un obsequio disminuye el inventario, pero no representa una venta.

Para los obsequios:

- Precio unitario: No aplica
- Descuento: No aplica
- Total: No aplica

---

### RB-022 — Destinatario de obsequios

El sistema debe permitir registrar el destinatario o referencia del obsequio.

El destinatario puede ser:

- Una persona
- Una organización
- Público general
- Otro

No debe ser obligatorio identificar personalmente a una persona cuando el contexto no lo permita.

---

### RB-023 — Observaciones de obsequios

Los obsequios deben permitir registrar observaciones adicionales.

Ejemplo:

"Obsequios entregados durante Festival de Cacao 2026."

---

## 11. Consumo interno

### RB-024 — Registro de consumo interno

El consumo interno disminuye el inventario, pero no representa una venta.

Para el consumo interno:

- Precio unitario: No aplica
- Descuento: No aplica
- Total: No aplica

---

### RB-025 — Tipo de consumo interno

El sistema debe permitir seleccionar el motivo o uso del producto.

Opciones iniciales:

- Muestras a proveedores
- Muestras a clientes
- Degustación
- Reunión o actividad interna
- Consumo del personal
- Otro

Cuando se seleccione "Otro", debe poder registrarse información adicional en observaciones.

---

## 12. Ventas

### RB-026 — Información de una venta

Cada venta debe conservar como mínimo:

- Fecha
- Producto
- Lote
- Cantidad
- Precio unitario
- Descuento
- Total
- Ubicación
- Responsable

---

### RB-027 — Precio variable en ventas

El precio unitario de una venta puede ser diferente al precio de referencia del producto.

El sistema debe permitir registrar el precio real aplicado en cada operación.

---

## 13. Ferias y eventos

### RB-028 — Feria como ubicación temporal

Una feria o evento puede registrarse como una ubicación temporal de inventario.

Ejemplo:

"Feria del Cacao 2026"

Mientras el evento esté activo, el sistema debe permitir consultar las unidades disponibles en dicha ubicación.

---

### RB-029 — Entrada de productos a una feria

Los productos pueden ser trasladados a una feria desde cualquier ubicación autorizada.

Aunque normalmente el producto salga de Bodega, el sistema no debe asumir que Bodega es el único origen posible.

Ejemplos:

- Bodega → Feria
- Vitrina → Feria
- Distribuidor → Feria

---

### RB-030 — Ventas durante una feria

Las ventas realizadas durante una feria deben registrarse como ventas y no como traslados.

La ubicación de origen de la venta será la ubicación temporal correspondiente al evento.

El precio aplicado puede ser diferente al precio habitual del producto.

---

### RB-031 — Obsequios durante una feria

Los productos entregados gratuitamente durante una feria deben registrarse como obsequios.

El precio, descuento y total serán:

- No aplica
- No aplica
- No aplica

---

### RB-032 — Sobrantes de una feria

Al finalizar una feria, las unidades sobrantes deben trasladarse a una ubicación de destino definida.

El destino puede ser:

- Bodega
- Vitrina
- Distribuidor
- Otra ubicación autorizada

Las unidades sobrantes no deben desaparecer del inventario.

---

## 14. Usuarios

### RB-033 — Usuarios iniciales

StockFlow debe contemplar inicialmente diferentes perfiles de usuario.

Perfiles considerados:

- Encargado o agente comercial
- Gerencia
- Área contable

Actualmente, el registro principal de movimientos es realizado por el agente comercial.

El acceso directo de los distribuidores al sistema queda pendiente de definición.

---

## 15. Reportes

### RB-034 — Conservación de información histórica

La información registrada debe conservarse para permitir la generación de reportes y análisis posteriores.

Los datos de producción, movimientos, ventas, devoluciones, obsequios, consumo interno, ubicaciones, lotes y vencimientos deben poder utilizarse para consultas y reportes.

---

## 16. Principios generales

### RB-035 — Inventario físico y económico

StockFlow debe diferenciar entre:

- Movimiento físico del producto
- Movimiento comercial o económico

No todo movimiento de inventario representa una venta.

---

### RB-036 — Trazabilidad

Cada movimiento debe permitir identificar qué ocurrió, cuándo ocurrió, con qué producto y lote, qué cantidad estuvo involucrada, desde dónde salió, hacia dónde fue y quién lo registró.

---

### RB-037 — Adaptabilidad

El sistema debe permitir agregar nuevas ubicaciones, productos, distribuidores, tipos de movimiento y motivos sin necesidad de modificar directamente la estructura principal del sistema cada vez que aparezca una nueva necesidad del negocio.

---

## Estado del documento

Estas reglas corresponden al levantamiento inicial realizado con base en el funcionamiento actual de COMTUMAC.

Las reglas pueden modificarse, ampliarse o complementarse durante el proceso de levantamiento de requisitos y validación con los usuarios.
