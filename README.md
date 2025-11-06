# Proyecto: Sistema Básico de Ventas para Farmacia

## 📋 Resumen Ejecutivo
El objetivo es desarrollar una aplicación web para gestionar el inventario y las ventas de una farmacia. La característica crítica que diferencia este sistema de una tienda común es el **control de stock por lotes y fechas de vencimiento**, asegurando que los medicamentos próximos a vencer se vendan primero.

## 🔄 Flujo de Trabajo Principal

### A. Entrada de Stock (Compras)
Cuando llega mercadería, el usuario no solo aumenta un contador genérico. Debe registrar:
1. Seleccionar el **Producto** (ej. Ibuprofeno).
2. Ingresar el **Código de Lote** y su **Fecha de Vencimiento** (datos impresos en la caja).
3. Ingresar la **Cantidad** recibida.
-> *Esto crea un nuevo registro en la tabla `lotes`.*

### B. Salida de Stock (Ventas)
1. El cajero selecciona un producto.
2. El sistema busca automáticamente el lote con `stock_actual > 0` que tenga la **fecha de vencimiento más próxima**.
3. Al confirmar la venta, se descuenta la cantidad de ese lote específico.


# Esquema de Base de Datos - Farmacia Simple

## 1. Tabla Productos
| id_producto | nombre | descripcion | precio | stock | fecha_vencimiento |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Paracetamol 500mg | Analgésico y antipirético | 5.50 | 100 | 2025-12-31 |
| 2 | Ibuprofeno 400mg | Antiinflamatorio no esteroideo | 8.00 | 50 | 2024-10-15 |
| 3 | Amoxicilina 500mg | Antibiótico de amplio espectro | 25.00 | 30 | 2025-06-01 |
| 4 | Loratadina 10mg | Antihistamínico para alergias | 4.50 | 75 | 2026-01-20 |
| 5 | Vitamina C 1000mg | Suplemento vitamínico | 12.00 | 60 | 2025-09-30 |

## 2. Tabla Clientes
| id_cliente | nombre | telefono | direccion |
| :--- | :--- | :--- | :--- |
| 1 | Juan Pérez | 555-1234 | Av. Principal 123 |
| 2 | María Gómez | 555-5678 | Calle Secundaria 456 |
| 3 | Carlos López | 555-9012 | Plaza Central 789 |

## 3. Tabla Ventas
| id_venta | fecha_venta | id_cliente | total_venta |
| :--- | :--- | :--- | :--- |
| 1 | 2023-10-25 10:30:00 | 1 | 13.50 |
| 2 | 2023-10-25 11:15:00 | NULL | 5.50 |
| 3 | 2023-10-26 09:45:00 | 2 | 50.00 |
| 4 | 2023-10-26 15:20:00 | 3 | 12.00 |

## 4. Tabla Detalle_Venta
| id_detalle | id_venta | id_producto | cantidad | precio_unitario |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | 1 | 1 | 5.50 |
| 2 | 1 | 2 | 1 | 8.00 |
| 3 | 2 | 1 | 1 | 5.50 |
| 4 | 3 | 3 | 2 | 25.00 |
| 5 | 4 | 5 | 1 | 12.00 |
