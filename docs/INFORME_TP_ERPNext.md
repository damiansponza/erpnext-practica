# Trabajo Práctico Integrador — Sistemas de Gestión Empresarial

**Integrantes:** Damian Sponza, Elian Montenegro y Antonio Melini  
**Empresa:** Luz del Centro SRL  
**Actividad:** Distribuidora de iluminación  
**Moneda:** ARS

## Datos generales del caso

El artículo utilizado en las operaciones fue **LED-E27-12W**, lámpara LED de 12 W con rosca E27, perteneciente al grupo Iluminación y con unidad de medida **Nos.**. El almacén utilizado para los movimientos fue **Depósito Central - LC - LDCS**. El artículo tiene habilitado Maintain Stock y no utiliza números de serie ni lotes.

Trabajamos con un costo uniforme de **ARS 3.000,00** por unidad y un sistema de inventario perpetuo. Los precios del caso son ficticios y no incluyen impuestos, descuentos ni cargos. Las compras y ventas se realizaron a crédito con plazo de 30 días. Los pagos y cobros no se registraron porque eran opcionales.

## Inicialización del stock

La consigna establece que el stock inicial (**S**) se calcula sumando las dos últimas cifras de los DNI de los integrantes. Para nuestro grupo, el cálculo fue el siguiente:

| Integrante | DNI | Terminación considerada |
|---|---:|---:|
| Damian Sponza | 31.050.632 | 32 |
| Elian Montenegro | 42.923.309 | 09 |
| Antonio Melini | 43.647.136 | 36 |
| **Stock inicial (S)** |  | **77 unidades** |

En ERPNext registramos la apertura mediante un documento **Stock Reconciliation**, con propósito **Opening Stock**, por 77 unidades del artículo LED-E27-12W, a una tasa de valuación de ARS 3.000,00. El valor inicial del inventario fue de **ARS 231.000,00**. El documento se confirmó antes de realizar los demás movimientos y no volvimos a cargar el stock inicial al registrar la compra.

- **ID:** `MAT-RECO-2026-00001`
- **Fecha:** 15-11-2026
- **Estado:** Submitted / Validado
- **Cantidad:** 77 Nos.
- **Tasa de valuación:** ARS 3.000,00
- **Valor total:** ARS 231.000,00
- **Centro de costos:** Principal - LDCS
- **Cuenta utilizada para la diferencia:** `1.1.1.01.01 - Caja - LDCS`

La cuenta consignada es la que figura en el comprobante registrado en ERPNext. Se deja identificada expresamente para distinguirla de la cuenta Temporary Opening indicada como referencia en la consigna.

## 1. Actividad 1 — Cliente captado desde Lead: Ferretería Horizonte SRL

### Situación y objetivo

Trabajamos la consulta de **Lucía Paredes**, responsable de compras de Ferretería Horizonte SRL, quien se comunicó desde el sitio web para solicitar 20 lámparas LED-E27-12W. La entrega se acordó en Córdoba. Los datos ficticios utilizados fueron `lucia@horizonte.example` y Calle de Práctica 100, Córdoba, Argentina.

El objetivo fue convertir la consulta en un cliente y generar un Sales Order, conservando el origen comercial en el Lead.

### Desarrollo en ERPNext

1. Revisamos posibles duplicados por organización y correo y creamos el **Lead**, con fuente Website, territorio Córdoba y responsable asignado.
2. Registramos la interacción simulada: “Se confirma necesidad de 20 lámparas LED 12 W E27, interlocutora de compras y entrega en Córdoba”. También dejamos indicada la próxima acción, su responsable y fecha.
3. Consideramos calificado el Lead porque se identificó una necesidad concreta y cuantificada, la interlocutora pertenece al área de compras, se confirmó el destino de entrega y aceptó recibir una oferta.
4. Creamos la **Opportunity** desde el Lead, conservando el origen y cargando 20 unidades a ARS 4.500,00, junto con la fecha estimada de cierre y la próxima acción.
5. Desde la oportunidad generamos y confirmamos la **Quotation** dirigida al Lead. Incluimos 20 unidades a ARS 4.500,00, una vigencia de siete días y condiciones de pago a 30 días. Simulamos la comunicación mediante una nota y registramos la aceptación.
6. Creamos el **Customer Ferretería Horizonte SRL** desde el Lead, con grupo Empresas, territorio Córdoba, moneda ARS y condiciones de pago a 30 días. Vinculamos Contact y Address sin duplicarlos. El flujo quedó consolidado en la ficha vinculada al Lead **Ferretería Horizonte SRL - 1**, sin utilizar el registro duplicado.
7. Desde la cotización creamos y confirmamos el **Sales Order** por 20 unidades a ARS 4.500,00 cada una. La entrega quedó prevista para el 24-11-2026 en el depósito Central.

**Resultado:**

- **Sales Order:** `SAL-ORD-2026-00001`
- **Cantidad:** 20 unidades
- **Precio unitario:** ARS 4.500,00
- **Total:** ARS 90.000,00
- **Estado al momento del registro:** Para entregar y facturar

## 2. Actividad 2 — Cliente captado desde Prospect: Instalaciones Nova SRL

### Situación y objetivo

Identificamos a **Instalaciones Nova SRL**, con domicilio en Avenida del Taller 200, Rosario, Argentina, como una cuenta objetivo. No existía una consulta entrante previa. A partir de una reunión comercial simulada detectamos la necesidad de 10 lámparas LED-E27-12W.

Consideramos a Nova una cuenta objetivo por su actividad vinculada con instalaciones eléctricas y por la posibilidad de una demanda recurrente de productos de iluminación. Identificamos dos interlocutores: Mariano Vega, del área de Compras, y Carla Sosa, de Administración.

### Desarrollo en ERPNext

1. Revisamos duplicados y creamos el **Prospect Instalaciones Nova SRL**, con territorio Rosario, responsable asignado y justificación como cuenta objetivo.
2. Creamos o vinculamos los contactos **Mariano Vega** (`mariano@nova.example`), con rol Compras, y **Carla Sosa** (`carla@nova.example`), con rol Administración. También registramos una dirección de facturación y entrega en Rosario.
3. Registramos la reunión simulada: “Mariano solicita 10 lámparas; Carla validará los datos de facturación”.
4. Creamos la **Opportunity** desde el Prospect, con 10 lámparas a ARS 4.500,00, fecha estimada y próxima acción.
5. Desde la oportunidad generamos y confirmamos la **Quotation**, con vigencia de siete días y condiciones de pago a 30 días. Registramos mediante una nota la comunicación y la aceptación.
6. Creamos el **Customer Instalaciones Nova SRL** desde el Prospect, con grupo Empresas, territorio Rosario, moneda ARS y condiciones a 30 días. Mantuvimos un único Customer y reutilizamos los contactos y las direcciones existentes.
7. Desde la cotización original creamos y confirmamos el **Sales Order** por 10 unidades a ARS 4.500,00 cada una.

**Resultado:**

- **Sales Order:** `SAL-ORD-2026-00002`
- **Cantidad:** 10 unidades
- **Precio unitario:** ARS 4.500,00
- **Total:** ARS 45.000,00
- **Fecha del pedido:** 18-11-2026
- **Fecha de entrega:** 25-11-2026
- **Estado al momento del registro:** Para entregar y facturar

## 3. Actividad 3 — Compra de lámparas LED a Fábrica Lumina SA

### Necesidad de reposición

Registramos una compra programada de **50 lámparas LED-E27-12W** a **Fábrica Lumina SA**, perteneciente al grupo Fabricantes. El precio acordado fue de ARS 3.000,00 por unidad, sin impuestos ni cargos, con vigencia de siete días y pago a 30 días.

La reposición permitió atender los 30 artículos comprometidos en los Sales Orders de Horizonte y Nova y ampliar en 20 unidades la reserva respecto del stock inicial de 77 unidades.

Aceptamos la oferta única del caso porque cubría el artículo y la cantidad requeridos, permitía cumplir las fechas previstas para la reposición y las entregas, y ofrecía condiciones de crédito a 30 días sin cargos adicionales.

### Desarrollo y trazabilidad en ERPNext

1. Verificamos los datos del Supplier Fábrica Lumina SA, sus Contact y Address, el stock inicial y los dos Sales Orders. No volvimos a inicializar el inventario.
2. Creamos y confirmamos una **Material Request** de tipo Purchase por 50 unidades, con fecha requerida y destino Depósito Central - LC - LDCS.
3. Desde la solicitud generamos la **Request for Quotation (RFQ)** para Fábrica Lumina SA. Dejamos desmarcada la opción Send Email en la fila del proveedor y simulamos la comunicación mediante una nota.
4. Desde la RFQ creamos y confirmamos la **Supplier Quotation** por 50 unidades a ARS 3.000,00, con vigencia de siete días y condiciones de pago a 30 días.
5. Desde la oferta generamos y confirmamos la **Purchase Order** para Luz del Centro SRL y Fábrica Lumina SA.

**Purchase Order:**

- **ID:** `PUR-ORD-2026-00001`
- **Fecha de emisión:** 19-11-2026
- **Cantidad:** 50 Nos.
- **Precio unitario:** ARS 3.000,00
- **Total:** ARS 150.000,00
- **Fecha requerida:** 24-11-2026
- **Almacén:** Depósito Central - LC - LDCS
- **Vencimiento:** 19-12-2026
- **Estado:** Submitted / Confirmada

6. Desde la orden creamos y confirmamos la **Purchase Receipt** por las 50 unidades aceptadas, sin unidades rechazadas, destinadas al almacén Depósito Central - LC - LDCS.

**Purchase Receipt:**

- **ID:** `MAT-PRE-2026-00001`
- **Fecha:** 19-11-2026
- **Cantidad aceptada:** 50 unidades
- **Cantidad rechazada:** 0 unidades
- **Estado:** Completado / Confirmado

7. Consultamos Stock Ledger y Stock Balance. Después de la recepción, el stock del artículo en el almacén central pasó de 77 a 127 unidades.
8. Desde la recepción generamos y confirmamos la **Purchase Invoice**, manteniendo Update Stock desactivado para evitar duplicar el ingreso de mercadería.

**Purchase Invoice:**

- **Número de comprobante:** `FAC-LED-G01-001`
- **Fecha de factura:** 19-11-2026
- **Vencimiento:** 19-12-2026
- **Cantidad:** 50 unidades
- **Precio unitario:** ARS 3.000,00
- **Total:** ARS 150.000,00
- **Update Stock:** Desactivado
- **Estado:** Confirmada, con saldo pendiente de ARS 150.000,00

**Resultado de la compra:** la Purchase Order figura completada, con el 100 % recibido y el 100 % facturado. La factura conserva un saldo pendiente de ARS 150.000,00, con vencimiento el 19-12-2026.

## 4. Actividad 4 — Entrega y facturación de ventas

Para esta actividad utilizamos los Sales Orders generados en las actividades anteriores: 20 unidades para Ferretería Horizonte SRL y 10 unidades para Instalaciones Nova SRL. Antes de los despachos, el stock disponible en el almacén central era de 127 unidades, luego de la recepción de compra.

### 4.1. Ferretería Horizonte SRL

Desde el Sales Order `SAL-ORD-2026-00001` creamos y confirmamos la **Delivery Note** por 20 lámparas, con destino Córdoba y salida desde Depósito Central - LC - LDCS.

- **Delivery Note:** `MAT-DN-2026-00001`
- **Cantidad entregada:** 20 unidades
- **Stock después de la entrega:** 107 unidades (127 - 20)

Luego generamos y confirmamos la **Sales Invoice** correspondiente:

- **Sales Invoice:** `ACC-SINV-2026-00001`
- **Fecha de contabilización:** 21-11-2026
- **Vencimiento:** 21-12-2026
- **Cantidad:** 20 unidades
- **Precio unitario:** ARS 4.500,00
- **Total:** ARS 90.000,00
- **Update Stock:** Desactivado
- **Saldo pendiente de cobro:** ARS 90.000,00

Como la salida de inventario ya se registró mediante la Delivery Note, la factura no generó una segunda disminución del stock. Por eso, después de la factura el saldo se mantuvo en 107 unidades.

### 4.2. Instalaciones Nova SRL

Desde el Sales Order `SAL-ORD-2026-00002` creamos y confirmamos la **Delivery Note** por 10 lámparas, con destino Avenida del Taller 200, Rosario, Santa Fe, y salida desde Depósito Central - LC - LDCS.

- **Delivery Note:** `MAT-DN-2026-00002`
- **Fecha:** 21-11-2026
- **Cantidad entregada:** 10 unidades
- **Stock después de la entrega:** 97 unidades (107 - 10)

Luego generamos y confirmamos la **Sales Invoice** correspondiente:

- **Sales Invoice:** `ACC-SINV-2026-00002`
- **Fecha de contabilización:** 21-11-2026
- **Vencimiento:** 21-12-2026
- **Cantidad:** 10 unidades
- **Precio unitario:** ARS 4.500,00
- **Total:** ARS 45.000,00
- **Update Stock:** Desactivado
- **Saldo pendiente de cobro:** ARS 45.000,00

La factura no generó otra salida de inventario porque el movimiento ya había sido registrado con la Delivery Note. Por lo tanto, el stock se mantuvo en 97 unidades.

### 4.3. Estado de los pedidos

Los dos Sales Orders quedaron completamente entregados y facturados. Las facturas permanecen pendientes de cobro porque no se registraron pagos, dado que estos eran opcionales en el caso.

## 5. Comparación entre el valor facturado y el costo de las lámparas entregadas

El total facturado por las dos ventas fue de **ARS 135.000,00**, correspondiente a 30 unidades vendidas a ARS 4.500,00 cada una:

| Cliente | Unidades | Precio unitario | Total facturado |
|---|---:|---:|---:|
| Ferretería Horizonte SRL | 20 | ARS 4.500,00 | ARS 90.000,00 |
| Instalaciones Nova SRL | 10 | ARS 4.500,00 | ARS 45.000,00 |
| **Total** | **30** | | **ARS 135.000,00** |

El costo de las 30 unidades entregadas fue de **ARS 90.000,00**, calculado a ARS 3.000,00 por unidad:

- Primera entrega: 20 × ARS 3.000,00 = ARS 60.000,00.
- Segunda entrega: 10 × ARS 3.000,00 = ARS 30.000,00.
- **Costo total de ventas: ARS 90.000,00.**

El inventario se reduce al costo de adquisición y no al precio de venta porque trabajamos con un sistema de inventario perpetuo y valuación al costo. Al despachar la mercadería, disminuye el activo Inventario por el costo de incorporación de los bienes y ese importe se reconoce como costo de ventas. El precio de venta se registra como ingreso. La diferencia entre ambos importes representa el margen bruto de la operación.

## 6. Conciliación de stock y diferencia del conteo físico

La evolución del inventario registrada para LED-E27-12W en Depósito Central - LC - LDCS fue la siguiente:

| Movimiento | Variación | Stock resultante |
|---|---:|---:|
| Apertura (`MAT-RECO-2026-00001`) | +77 | 77 |
| Recepción de compra (`MAT-PRE-2026-00001`) | +50 | 127 |
| Entrega a Ferretería Horizonte (`MAT-DN-2026-00001`) | -20 | 107 |
| Entrega a Instalaciones Nova (`MAT-DN-2026-00002`) | -10 | 97 |
| **Saldo según ERPNext** | | **97** |
| **Conteo físico indicado en el caso** | | **95** |

El enunciado establece que el conteo físico final debe ser **S + 18**. Como nuestro stock inicial fue de 77 unidades, el conteo físico indicado es de 95 unidades. Sin embargo, los movimientos registrados en ERPNext arrojan un saldo de 97 unidades.

La diferencia es de **2 unidades** entre el saldo del sistema y el conteo físico indicado. Dejamos documentada esta discrepancia para su análisis de control interno y auditoría, sin realizar un ajuste automático que oculte la diferencia.

## 7. Resumen de saldos comerciales y contables

| Documento / concepto | Importe | Situación informada |
|---|---:|---|
| Purchase Invoice — Fábrica Lumina SA | ARS 150.000,00 | Pendiente de pago |
| Sales Invoice — Ferretería Horizonte SRL | ARS 90.000,00 | Pendiente de cobro |
| Sales Invoice — Instalaciones Nova SRL | ARS 45.000,00 | Pendiente de cobro |
| **Total de ventas** | **ARS 135.000,00** | |
| **Costo de las 30 unidades vendidas** | **ARS 90.000,00** | |

## 8. Estado final y disponibilidad para el coloquio

Al finalizar las operaciones, los Sales Orders `SAL-ORD-2026-00001` y `SAL-ORD-2026-00002` figuran completados, con el 100 % de las unidades entregadas y el 100 % facturadas. Las facturas de venta conservan sus saldos pendientes de cobro y la factura de compra conserva el saldo pendiente de pago correspondiente.

Los documentos, movimientos de stock y saldos informados se encuentran registrados en la instancia de ERPNext del GitHub Codespace utilizada para este trabajo práctico. Esa misma instancia es la que se utilizará para la presentación y defensa en el coloquio.
