# Data Warehouse Northwind - Implementación Completa

## 📋 Descripción del Proyecto
Implementación de un Data Warehouse para la base de datos Northwind utilizando modelo dimensional. Este proyecto incluye todo el proceso ETL (Extract, Transform, Load) para cargar y transformar datos operacionales en un almacén de datos analítico.

## 🏗️ Estructura del Data Warehouse

### Tablas Dimensionales (Dimensions)
1. **DimCustomers** - Información de clientes (91 registros)
   - CustomerKey (PK): Identificador único
   - CustomerID: Código original del cliente
   - CustomerName: Nombre de la empresa
   - ContactName: Persona de contacto
   - City, Country: Ubicación

2. **DimEmployees** - Información de empleados (9 registros)
   - EmployeeKey (PK): Identificador único
   - EmployeeID: Código original
   - EmployeeName: Nombre completo
   - Title: Cargo
   - HireDate: Fecha de contratación

3. **DimShippers** - Transportistas (3 registros)
   - ShipKey (PK): Identificador único
   - ShipID: Código original
   - ShipName: Nombre de la empresa
   - Phone: Teléfono

### Tabla de Hechos (Fact Table)
4. **FactOrders** - Pedidos realizados (830 registros)
   - OrderKey (PK): Identificador único
   - OrderDetailsID: Número de pedido original
   - CustomerID (FK): Referencia a DimCustomers
   - EmployeeID (FK): Referencia a DimEmployees
   - OrderDate: Fecha del pedido
   - ShipID (FK): Referencia a DimShippers
   - Freight: Costo de envío

## 🔄 Proceso ETL Implementado

### Extracción (Extract)
- Datos extraídos desde la base de datos Northwind original
- Tablas fuente: Customers, Employees, Shippers, Orders

### Transformación (Transform)
- Creación de claves sustitutivas (surrogate keys)
- Unión de campos (ej: FirstName + LastName)
- Mapeo de claves foráneas
- Estructuración en modelo dimensional

### Carga (Load)
- Carga incremental de dimensiones
- Carga de tabla de hechos con integridad referencial
- Validación de datos cargados

## 📁 Scripts SQL Incluidos

1. **`01_creacion_tablas.sql`** - Creación de la estructura del DW
2. **`02_carga_dimensiones.sql`** - Carga de tablas dimensionales
3. **`03_carga_fact_orders.sql`** - Carga de la tabla de hechos
4. **`04_consultas_verificacion.sql`** - Consultas de validación

## 📊 Resultados de Carga

| Tabla | Registros Cargados | Estado |
|-------|-------------------|---------|
| DimCustomers | 91 | ✅ |
| DimEmployees | 9 | ✅ |
| DimShippers | 3 | ✅ |
| FactOrders | 830 | ✅ |

🛠️ Requisitos Técnicos

- Base de datos fuente: Northwind (Microsoft Sample Database)
- Motor de base de datos: SQL Server
- Herramienta: SQL Server Management Studio (SSMS)
- Proceso: ETL manual mediante scripts SQL

 Cómo Ejecutar

1. Ejecutar `01_creacion_tablas.sql` para crear la estructura
2. Ejecutar `02_carga_dimensiones.sql` para cargar dimensiones
3. Ejecutar `03_carga_fact_orders.sql` para cargar hechos
4. Ejecutar `04_consultas_verificacion.sql` para verificar

