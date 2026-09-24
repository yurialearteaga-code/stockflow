# Reglas de Negocio — StockFlow

**Proyecto:** StockFlow  
**Versión:** 1.0  
**Estado:** Oficial – Levantamiento inicial  
**Caso de referencia:** COMTUMAC

---

## 1. Inventario y propiedad

### RB-001 — Inventario real de la empresa

El inventario real corresponde a todas las unidades de producto que continúan siendo propiedad de la empresa, independientemente de la ubicación física en la que se encuentren.


---

### RB-002 — Inventario por ubicación

StockFlow debe permitir consultar las cantidades disponibles por ubicación, además del inventario total de la empresa.

Las ubicaciones pueden ser permanentes o temporales.

---

### RB-003 — Propiedad independiente de la ubicación

La ubicación física de un producto no determina por sí sola un cambio de propiedad.

Un producto ubicado en un distribuidor o feria puede continuar perteneciendo a la empresa.

---

### RB-004 — Actualización automática del inventario

Todo movimiento autorizado que implique entrada, salida o cambio de ubicación debe actualizar las cantidades correspondientes del inventario.

No se debe modificar directamente el saldo del inventario sin una operación que permita identificar el motivo y conservar su trazabilidad.

---

### RB-005 — Inventario negativo

StockFlow no debe permitir que una operación genere cantidades negativas de inventario, salvo que posteriormente se defina y autorice explícitamente una excepción de negocio.

---

## 2. Productos

### RB-006 — Identificación del producto

Cada producto debe contar con una identificación interna dentro de StockFlow.
El código del producto será definido por la empresa.

---

### RB-007 — Código independiente del sistema contable

El código interno utilizado por StockFlow no debe depender del código utilizado por el sistema contable de la empresa.
StockFlow debe poder funcionar con su propia identificación de productos.

---

### RB-008 — Estado del producto

Los productos deben poder encontrarse activos o inactivos.

---

### RB-009 — Inactivación de productos con historial

Un producto que tenga movimientos, ventas, producción u otra información histórica no debe eliminarse físicamente.
Cuando deje de utilizarse, debe ser inactivado para conservar su historial.

---

## 3. Producción y transformación

### RB-010 — Registro de producción

Cada producción debe quedar registrada y asociada como mínimo a:

- Fecha.
- Producto.
- Lote.
- Cantidad de materia prima utilizada, cuando aplique.
- Cantidad producida.
- Fecha de vencimiento, cuando aplique.
- Responsable.
- Observaciones.

---

### RB-011 — Entrada del producto terminado

El producto terminado resultante de una producción debe ingresar al inventario de StockFlow.
Inicialmente, el destino habitual del producto terminado será Bodega.

---

### RB-012 — Cantidad producida

La cantidad producida es la cantidad de unidades terminadas que ingresa al inventario.
La cantidad de materia prima utilizada se conserva como información de trazabilidad y no representa por sí misma unidades de producto terminado.

---

### RB-013 — Transformación externa

La transformación puede ser realizada por un tercero.
StockFlow debe registrar la información operativa necesaria para controlar la producción, pero no reemplaza el proceso contable asociado al servicio de transformación.

---

### RB-014 — Costos contables de producción

El cálculo y control de costos contables de producción o transformación queda fuera del alcance inicial de StockFlow.

---

## 4. Lotes

### RB-015 — Identificación por lote

Cuando un producto maneje lotes, cada producción debe estar asociada a un lote identificable.

---

### RB-016 — Relación producto-lote

Un lote debe estar asociado a un producto específico.

---

### RB-017 — Trazabilidad por lote

Las operaciones relacionadas con productos que manejan lote deben permitir identificar el lote involucrado.

Esto incluye, cuando corresponda:

- Producción.
- Traslados.
- Ventas.
- Devoluciones.
- Obsequios.
- Consumo interno.
- Ajustes.

---

### RB-018 — Fecha de vencimiento

Cuando un producto maneje vencimiento, el lote debe conservar su fecha de vencimiento.

---

### RB-019 — Producción de nuevos lotes

Cada nueva producción que corresponda a un nuevo lote debe registrarse como una operación independiente para permitir su trazabilidad.

---

## 5. Vencimientos y alertas

### RB-020 — Alerta de vencimiento a 60 días

StockFlow debe generar una alerta cuando un lote se encuentre a 60 días de su fecha de vencimiento.

---

### RB-021 — Alerta de vencimiento a 30 días

StockFlow debe generar una alerta cuando un lote se encuentre a 30 días de su fecha de vencimiento.

---

### RB-022 — Información de la alerta

Las alertas de vencimiento deben permitir identificar como mínimo:

- Producto.
- Lote.
- Cantidad disponible.
- Ubicación.
- Fecha de vencimiento.

---

### RB-023 — Estado de vencimiento

El sistema debe permitir diferenciar entre productos:

- Vigentes.
- Próximos a vencer.
- Vencidos.

---

## 6. Ubicaciones

### RB-024 — Ubicaciones configurables

StockFlow debe permitir registrar y administrar diferentes ubicaciones de inventario.

---

### RB-025 — Tipos de ubicación

Las ubicaciones pueden clasificarse, entre otras, como:

- Permanente.
- Temporal.
- Bodega.
- Vitrina.
- Distribuidor.
- Feria o evento.

---

### RB-026 — Inventario por ubicación

El sistema debe permitir consultar qué productos, lotes y cantidades se encuentran en cada ubicación.

---

## 7. Traslados

### RB-027 — Traslado de inventario

Un traslado representa un cambio de ubicación física del producto y no constituye una venta.

---

### RB-028 — Conservación de propiedad durante un traslado

Un traslado no modifica la propiedad del producto.

Por ejemplo:

**Bodega → Distribuidor**

continúa siendo inventario propiedad de la empresa.

---

### RB-029 — Información del traslado

Todo traslado debe registrar como mínimo:

- Fecha.
- Producto.
- Lote, cuando aplique.
- Cantidad.
- Ubicación de origen.
- Ubicación de destino.
- Responsable.
- Observaciones.

---

### RB-030 — Actualización por traslado

Al realizar un traslado:

- Se disminuye la cantidad de la ubicación de origen.
- Se aumenta la cantidad de la ubicación de destino.

El inventario total propiedad de la empresa no cambia por el traslado.

---

## 8. Distribuidores

### RB-031 — Producto entregado a distribuidores

Cuando la empresa entregue productos a un distribuidor mediante un traslado, las unidades continúan siendo propiedad de la empresa hasta que se produzca la venta correspondiente al distribuidor.

---

### RB-032 — Inventario en poder del distribuidor

Las unidades entregadas a un distribuidor deben permanecer identificadas dentro del inventario de la empresa y asociadas a la ubicación correspondiente.

---

### RB-033 — Reporte de ventas del distribuidor

El distribuidor puede informar las unidades que ha vendido a sus clientes.
El reporte de una venta realizada por el distribuidor no constituye automáticamente una venta de la empresa al distribuidor.

---

### RB-034 — Compra de unidades por parte del distribuidor

Cuando el distribuidor decida comprar o cancelar las unidades que tiene en su poder, debe registrarse una venta de la empresa al distribuidor.

---

### RB-035 — Nuevos pedidos del distribuidor

Cuando un distribuidor solicite nuevas unidades después de haber comprado unidades anteriores, las nuevas unidades deben registrarse mediante un nuevo traslado.

---

### RB-036 — Precio de reventa del distribuidor

StockFlow controla el precio de venta aplicado por la empresa.
El precio al que el distribuidor posteriormente venda el producto a sus propios clientes no forma parte del control de precios de StockFlow.

---

## 9. Ventas

### RB-037 — Registro individual de ventas

Cada venta debe registrarse como una operación independiente.

---

### RB-038 — Información de la venta

Una venta debe conservar como mínimo:

- Fecha.
- Producto.
- Lote, cuando aplique.
- Cantidad.
- Precio unitario.
- Descuento, cuando aplique.
- Total.
- Ubicación.
- Responsable.

---

### RB-039 — Precio de referencia

Un producto puede tener un precio base o de referencia.
Este precio no obliga a que todas las ventas se realicen al mismo valor.

---

### RB-040 — Precio real de venta

Cada venta debe conservar el precio realmente aplicado en la operación.
El precio puede variar según condiciones comerciales autorizadas.

---

### RB-041 — Cálculo del total

Cuando corresponda aplicar descuento, el total de la venta se calculará como:

**Total = (Cantidad × Precio unitario) − Descuento**

---

### RB-042 — Venta en feria

Las ventas realizadas durante una feria deben registrarse como ventas y no como traslados.
La ubicación de origen será la ubicación correspondiente al evento.

---

## 10. Ferias y eventos

### RB-043 — Feria como ubicación temporal

Una feria o evento puede registrarse como una ubicación temporal de inventario.

---

### RB-044 — Traslado hacia una feria

Los productos enviados a una feria deben registrarse mediante un traslado.

---

### RB-045 — Propiedad durante una feria

Los productos enviados a una feria continúan siendo propiedad de la empresa hasta que sean vendidos u objeto de otra operación autorizada.

---

### RB-046 — Ventas durante una feria

Las unidades vendidas durante una feria deben registrarse como ventas.

---

### RB-047 — Obsequios durante una feria

Las unidades entregadas gratuitamente durante una feria deben registrarse como obsequios y no como ventas.

---

### RB-048 — Sobrantes de una feria

Las unidades que no sean vendidas al finalizar una feria deben regresar mediante una operación registrada a una ubicación autorizada.
Los sobrantes no deben desaparecer del inventario.

---

## 11. Obsequios

### RB-049 — Obsequio como operación no comercial

Un obsequio disminuye el inventario, pero no representa una venta.

---

### RB-050 — Información del obsequio

Un obsequio debe registrar como mínimo:

- Fecha.
- Producto.
- Lote, cuando aplique.
- Cantidad.
- Destinatario o referencia.
- Responsable.
- Observaciones.

---

### RB-051 — Destinatario

El destinatario puede ser:

- Persona.
- Organización.
- Público general.
- Otro.

No será obligatorio registrar datos personales cuando el contexto no lo requiera.

---

## 12. Consumo interno

### RB-052 — Consumo interno

El consumo interno disminuye el inventario, pero no representa una venta.

---

### RB-053 — Motivo del consumo interno

El consumo interno debe permitir registrar el motivo o finalidad.

---

### RB-054 — Información del consumo interno

El consumo interno debe registrar como mínimo:

- Fecha.
- Producto.
- Lote, cuando aplique.
- Cantidad.
- Motivo.
- Responsable o receptor.
- Observaciones.

---

## 13. Devoluciones

### RB-055 — Registro de devolución

Las devoluciones deben registrarse como operaciones independientes y conservar su trazabilidad.

---

### RB-056 — Información de devolución

Una devolución debe permitir registrar:

- Producto.
- Lote.
- Cantidad.
- Fecha.
- Ubicación de origen.
- Ubicación de destino.
- Motivo.
- Responsable.
- Observaciones.

---

### RB-057 — Destino de una devolución

Una devolución no necesariamente debe regresar a Bodega.
Puede ingresar a cualquier ubicación autorizada.

---

### RB-058 — Motivos de devolución

El sistema debe permitir registrar el motivo de la devolución.
Inicialmente puede contemplarse:

- Reabastecimiento solicitado.
- Producto defectuoso.
- Producto vencido.
- Error en despacho.
- Otro.

---

## 14. Conteos físicos

### RB-059 — Realización de conteos

StockFlow debe permitir registrar conteos físicos del inventario.

---

### RB-060 — Comparación físico-sistema

El sistema debe permitir comparar la cantidad física encontrada con la cantidad registrada en StockFlow.

---

### RB-061 — Identificación de diferencias

Cuando exista diferencia entre el inventario físico y el sistema, esta debe quedar identificada y registrada.

---

### RB-062 — Revisión previa al ajuste

Antes de realizar un ajuste por diferencia de inventario, debe revisarse el historial de movimientos para identificar posibles operaciones no registradas o errores de registro.

---

### RB-063 — Ajuste autorizado

Cuando después de la revisión sea necesario modificar el saldo, el ajuste debe registrar como mínimo:

- Producto.
- Lote.
- Cantidad.
- Diferencia.
- Motivo.
- Responsable.
- Fecha.
- Observaciones.

---

## 15. Correcciones y anulaciones

### RB-064 — Corrección de información

StockFlow debe permitir corregir información de una operación cuando exista un error, de acuerdo con los permisos establecidos.

---

### RB-065 — Registro de modificaciones

Las modificaciones relevantes deben conservar información sobre:

- Usuario que realizó el cambio.
- Fecha y hora.
- Registro afectado.
- Información anterior, cuando corresponda.
- Nueva información.
- Motivo, cuando corresponda.

---

### RB-066 — Anulación de operaciones

Una operación incorrecta no debe eliminarse físicamente del historial.
Debe poder anularse o corregirse mediante un mecanismo que conserve la trazabilidad.

---

### RB-067 — Prohibición de eliminación del historial

No se deben eliminar movimientos históricos para ocultar o corregir una operación.

---

## 16. Usuarios y roles

### RB-068 — Usuario único

Una persona puede tener varios roles dentro de una misma cuenta.
No se debe crear una cuenta diferente únicamente porque una persona desempeñe más de un rol.

---

### RB-069 — Roles

StockFlow debe contemplar, inicialmente, roles como:

- Administrador.
- Responsable de inventario.
- Gerencia.
- Contabilidad.

Los permisos dependerán del rol asignado.

---

### RB-070 — Responsabilidad de las operaciones

Cada operación realizada en StockFlow debe poder asociarse al usuario responsable de registrarla.

---

### RB-071 — Distribuidores y acceso al sistema

El acceso directo de los distribuidores a StockFlow queda como una decisión pendiente de diseño y no constituye una condición obligatoria del MVP.

---

## 17. Multiempresa

### RB-072 — Independencia entre empresas

Cada empresa que utilice StockFlow debe mantener sus datos completamente independientes de las demás empresas.

---

### RB-073 — Aislamiento de información

Los usuarios de una empresa no deben poder consultar ni modificar información perteneciente a otra empresa.

Esto incluye:

- Usuarios.
- Productos.
- Lotes.
- Ubicaciones.
- Distribuidores.
- Movimientos.
- Ventas.
- Reportes.
- Configuración.

---

### RB-074 — Configuración independiente

Cada empresa debe administrar independientemente sus productos, ubicaciones, usuarios, distribuidores, parámetros y demás información operativa.

---

### RB-075 — Aislamiento en la aplicación

La separación entre empresas debe garantizarse desde la lógica del sistema y la base de datos, no únicamente desde la interfaz visual.

---

## 18. Auditoría y trazabilidad

### RB-076 — Trazabilidad de operaciones

Cada movimiento debe permitir identificar:

- Qué ocurrió.
- Cuándo ocurrió.
- Producto.
- Lote, cuando aplique.
- Cantidad.
- Origen.
- Destino.
- Responsable.

---

### RB-077 — Historial de operaciones

StockFlow debe conservar el historial de las operaciones realizadas.

---

### RB-078 — Auditoría de modificaciones

Las modificaciones relevantes deben quedar registradas para permitir conocer quién modificó la información, cuándo y qué información fue afectada.

---

### RB-079 — Historial no editable

Los registros de auditoría no deben poder modificarse libremente por los usuarios.

---

## 19. Reportes y consultas

### RB-080 — Información histórica

La información registrada debe conservarse para permitir consultas, análisis y generación de reportes.

---

### RB-081 — Inventario por dimensiones

StockFlow debe permitir consultar el inventario, como mínimo, por:

- Producto.
- Lote.
- Ubicación.

---

### RB-082 — Reportes de movimientos

El sistema debe permitir consultar los movimientos por períodos y tipos de operación.

---

### RB-083 — Reportes de ventas

El sistema debe permitir consultar las ventas por período y demás criterios autorizados.

---

### RB-084 — Reportes de distribuidores y eventos

La información relacionada con distribuidores, ferias y eventos debe poder consultarse para conocer las unidades entregadas, vendidas, disponibles y retornadas, según corresponda.

---

## 20. Stock mínimo

### RB-085 — Nivel mínimo de inventario

Cada producto podrá tener un nivel mínimo de inventario definido por la empresa.

---

### RB-086 — Alerta de inventario bajo

Cuando la cantidad disponible de un producto sea igual o inferior al nivel mínimo configurado, StockFlow debe generar una alerta.

---

## 21. Operaciones sin venta

### RB-087 — Diferenciación de operaciones

StockFlow debe diferenciar las operaciones comerciales de las operaciones que únicamente modifican el inventario.

Entre estas últimas se encuentran:

- Producción.
- Traslado.
- Obsequio.
- Consumo interno.
- Devolución.
- Ajuste.

---

### RB-088 — Operaciones sin ingreso por venta

Un traslado, obsequio, consumo interno o ajuste no debe registrarse como una venta ni generar ingresos por venta.

---

## 22. Contabilidad y alcance

### RB-089 — Independencia del sistema contable

StockFlow es un sistema de gestión y trazabilidad de inventario y no reemplaza el sistema contable de la empresa.

---

### RB-090 — Facturación

La gestión contable y de facturación permanece dentro de los procesos y sistemas correspondientes de la empresa.

---

### RB-091 — Información contable

StockFlow no debe exigir información contable que no sea necesaria para la gestión operativa del inventario.

---

### RB-092 — Integración futura

Una posible integración con sistemas contables podrá considerarse como una funcionalidad futura, sin constituir una dependencia del funcionamiento inicial de StockFlow.

---

## 23. Adaptabilidad

### RB-093 — Nuevos productos

El sistema debe permitir incorporar nuevos productos sin modificar la estructura principal de la aplicación.

---

### RB-094 — Nuevas ubicaciones

El sistema debe permitir incorporar nuevas ubicaciones según las necesidades de cada empresa.

---

### RB-095 — Nuevos tipos de operación

El diseño debe permitir incorporar nuevos tipos de movimientos u operaciones cuando aparezcan nuevas necesidades del negocio.

---

### RB-096 — Nuevos motivos

El sistema debe permitir incorporar nuevos motivos para operaciones como devoluciones, ajustes, consumo interno y otras operaciones.

---

# Estado del documento

**Versión:** 1.0  
**Estado:** Oficial – Levantamiento inicial.

Estas reglas de negocio constituyen la base para el diseño funcional de StockFlow y deberán ser consideradas posteriormente en:

- Levantamiento de requisitos.
- Casos de uso.
- Modelo de datos.
- Arquitectura.
- Diseño de la aplicación.
- Desarrollo y pruebas.

Las modificaciones futuras deberán registrarse mediante una nueva versión del documento.