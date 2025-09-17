Desarrollo del reto 02: \
Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno más diagramas tipo UML.

Ejemplo Usado: Tienda de lanas. \
Este programa permite: \
-Registrar distintos tipos de lanas que heredan unas caracteristicas especificas.\
-Mantener un inventario del stock de lanas disponibles.\
-Agregar clientes que támbien heredan ciertas caracteristicas.\
-Gestionar los pedidos de lanas que los clientes hagan.

```mermaid
classDiagram
direction TB
    class Tienda {
        -str nombre
        -str direccion
        +agregarLana(lana: Lana)
        +registrarCliente(Cliente) 
        +crearPedido(Cliente, lanas: List) Pedido
    }
    class Lana {
        -str marca
        -str color
        -str material
        -float grosor
        -float pesoGramos
        -int precio
        -int stock
        +actualizarStock(cantidad: int)
    }
    class Cliente {
        -str nombre
        -str email
        -str direccion
        +realizarPedido(lanas: List) Pedido
    }
    class Pedido {
        -int id
        -date fecha
        -str estado
        +confirmar()
        +cancelar()
    }
    class Inventario {
        -list lanas
        +consultarStock(marca: String, color: String) int
        +actualizarStock(marca: String, color: String, cantidad: int)
    }
    Tienda "1" *-- "*" Lana: Ofrece
    Tienda "1" *-- "*" Cliente: Gestiona
    Pedido "1" --> "*" Lana: Incluye
    Pedido "1" --> "1" Cliente: Pertenece
    Inventario "1" *-- "*" Lana: Controla
    class Tienda:::Class_01
    class Lana:::Class_01
    class Cliente:::Class_01
    class Pedido:::Class_01
    class Inventario:::Class_01
    classDef Class_01 color:#000000, stroke-width:4px, stroke-dasharray: 0, stroke:#2962FF, fill:#BBDEFB

```

