# Parte A: Taller mecánico

Asignación 1 - Mapeo de dominios a Prisma. MySQL 8 y Prisma 6.19.0.

## Respuesta

**¿Qué pasaría si intentaras borrar un Cliente que todavía tiene un Vehiculo?**

MySQL rechazaría el borrado porque `Vehiculo.clienteId` tiene una llave foránea hacia `Cliente.id` con `ON DELETE RESTRICT`. El cliente y sus vehículos permanecerían intactos: no se permite dejar vehículos sin un cliente válido. Para eliminarlo, primero habría que reasignar o eliminar sus vehículos, atendiendo también las órdenes y refacciones dependientes. La migración permite comprobar esta regla en la restricción `Vehiculo_clienteId_fkey`.

