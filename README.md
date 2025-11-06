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
