# Diagrama Entidad-Relación de StockLab

## Descripción

El sistema StockLab está formado por cinco entidades principales:

- Usuarios
- Productos
- Movimientos de inventario
- Ventas
- Detalle de ventas

## Diagrama

```mermaid
erDiagram

    USUARIOS ||--o{ VENTAS : realiza
    USUARIOS ||--o{ MOVIMIENTOS_INVENTARIO : registra
    PRODUCTOS ||--o{ MOVIMIENTOS_INVENTARIO : tiene
    VENTAS ||--o{ DETALLE_VENTAS : contiene
    PRODUCTOS ||--o{ DETALLE_VENTAS : aparece_en

    USUARIOS {
        int id PK
        string nombre
        string correo UK
        string password_hash
        datetime fecha_creacion
    }

    PRODUCTOS {
        int id PK
        string nombre
        string categoria
        decimal precio
        int stock
        int stock_minimo
        datetime fecha_creacion
    }

    MOVIMIENTOS_INVENTARIO {
        int id PK
        int producto_id FK
        int usuario_id FK
        string tipo
        int cantidad
        string nota
        datetime fecha
    }

    VENTAS {
        int id PK
        int usuario_id FK
        decimal subtotal
        decimal impuesto
        decimal total
        datetime fecha
    }

    DETALLE_VENTAS {
        int id PK
        int venta_id FK
        int producto_id FK
        int cantidad
        decimal precio_unitario
        decimal total
    }
 ```
## Explicación

La tabla USUARIOS se relaciona con VENTAS porque un usuario puede realizar varias ventas.

La tabla PRODUCTOS se relaciona con MOVIMIENTOS_INVENTARIO porque un producto puede tener varias entradas y salidas.

La tabla VENTAS se relaciona con DETALLE_VENTAS porque una venta puede incluir varios productos.
