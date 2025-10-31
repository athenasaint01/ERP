# Sistema ERP Integral

<div align="center">

**Sistema de Planificación de Recursos Empresariales para Empresas de Servicios**

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)

</div>

---

## 📋 Tabla de Contenidos

- [Descripción](#-descripción)
- [Características Principales](#-características-principales)
- [Stack Tecnológico](#-stack-tecnológico)
- [Arquitectura del Sistema](#-arquitectura-del-sistema)
- [Requisitos Previos](#-requisitos-previos)
- [Instalación](#-instalación)
- [Configuración](#-configuración)
- [Uso](#-uso)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [API Endpoints](#-api-endpoints)
- [Licencia](#-licencia)

---

## 🎯 Descripción

SPEAS es un sistema ERP completo diseñado específicamente para empresas de servicios en Perú. Desarrollado con tecnologías modernas, ofrece gestión integral de operaciones comerciales y financieras con énfasis en el cumplimiento normativo de SUNAT.

El sistema cubre el ciclo completo de negocio: desde la gestión de clientes y proveedores, pasando por la facturación y tesorería, hasta la contabilidad automatizada y la generación de reportes fiscales.

---

## ✨ Características Principales

### 📊 Dashboard Gerencial
- Visualización en tiempo real de KPIs empresariales
- Análisis de flujo de caja
- Rentabilidad por cliente y proyecto
- Gráficos interactivos con ApexCharts

### 👥 Módulo de Maestros
- **Clientes**: Gestión completa con seguimiento de saldos a favor
- **Proveedores**: Base de datos centralizada de proveedores
- **Servicios**: Catálogo de servicios con códigos y descripciones

### 💰 Ciclo de Ventas
- Creación y seguimiento de facturas de venta
- Cálculo automático de saldos pendientes
- Generación de XML para SUNAT
- Descarga de PDF y CDR
- Aplicación de saldos a favor

### 📦 Ciclo de Compras
- Registro de facturas de compra (obligaciones)
- Control de cuentas por pagar
- Seguimiento de vencimientos
- Generación automática de asientos contables

### 🏦 Módulo de Tesorería
- **Cuentas Bancarias**: Gestión de cuentas propias de la empresa
- **Pagos Realizados**: Registro y control de pagos a proveedores
- **Pagos Recibidos**: Control de cobros de clientes
- **Saldos a Favor**: Manejo de pagos anticipados de clientes

### 📚 Módulo de Contabilidad
- **Plan de Cuentas**: Personalizable según PCGE
- **Asientos Contables**: Generación automática desde ventas y compras
- **Balance de Comprobación**: Consulta de saldos por cuenta
- **Auditoría**: Registro completo de todas las transacciones

### 📁 Proyectos y Préstamos
- Seguimiento de proyectos por cliente
- Control de planes de pago de préstamos
- Asociación de ventas a proyectos específicos

### 📈 Reportes Financieros y Fiscales
- **Libros Electrónicos PLE**: Registro de Compras y Ventas para SUNAT
- **Estado de Resultados**: Por rango de fechas con análisis vertical
- **Balance General**: A una fecha de corte específica
- **Exportación**: Todos los reportes exportables a Excel

### 🔐 Configuración y Seguridad
- Sistema de autenticación con JWT
- Gestión de usuarios multiempresa
- Roles y permisos granulares
- Auditoría completa de acciones del sistema

---

## 🛠 Stack Tecnológico

### Backend
| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| **TypeScript** | 5.8.x | Lenguaje principal |
| **Node.js** | 18+ | Entorno de ejecución |
| **Express.js** | 5.x | Framework web |
| **PostgreSQL** | 14+ | Base de datos |
| **pg** | 8.x | Cliente PostgreSQL |
| **JWT** | 9.x | Autenticación |
| **bcryptjs** | 3.x | Hashing de contraseñas |
| **PDFKit** | 0.17.x | Generación de PDFs |
| **xlsx** | 0.18.x | Exportación a Excel |
| **xmlbuilder2** | 3.x | Generación de XML para SUNAT |

### Frontend
| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| **TypeScript** | 5.8.x | Lenguaje principal |
| **React** | 19.x | Framework UI |
| **Vite** | 7.x | Build tool y dev server |
| **React Router** | 7.x | Enrutamiento SPA |
| **Axios** | 1.x | Cliente HTTP |
| **ApexCharts** | 5.x | Gráficos interactivos |
| **Lucide React** | - | Iconografía |
| **SweetAlert2** | 11.x | Notificaciones |

---

## 🏗 Arquitectura del Sistema

### Backend - Arquitectura en Capas

```
┌─────────────────────────────────────────┐
│           HTTP Request                  │
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│  Routes Layer (*.routes.ts)             │
│  - Define endpoints                     │
│  - Apply middleware (auth, permissions) │
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│  Controllers Layer (*.controller.ts)    │
│  - Handle HTTP req/res                  │
│  - Validate input                       │
│  - Orchestrate business logic           │
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│  Services Layer (*.service.ts)          │
│  - Business logic implementation        │
│  - Database operations                  │
│  - Transaction management               │
│  - Automatic accounting entries         │
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│         PostgreSQL Database             │
└─────────────────────────────────────────┘
```

### Frontend - Arquitectura de Componentes

```
┌─────────────────────────────────────────┐
│          App.tsx (Router)               │
└─────────┬───────────────────────────────┘
          │
          ├─► ProtectedRoute (Auth Guard)
          │
┌─────────▼───────────────────────────────┐
│  Pages (Feature Modules)                │
│  - Dashboard                            │
│  - Ventas, Compras, Tesorería           │
│  - Contabilidad, Reportes               │
└─────────┬───────────────────────────────┘
          │
          ├─► Components (Shared UI)
          ├─► Services (API Calls)
          ├─► Context (Global State)
          └─► Hooks (Custom Logic)
```

---

## 📦 Requisitos Previos

Asegúrate de tener instalado:

- **Node.js** 18.0.0 o superior
- **npm** 9.0.0 o superior (o **yarn**)
- **PostgreSQL** 14.0 o superior
- **Git** (opcional, para clonar el repositorio)

---

## 🚀 Instalación

### 1. Clonar el Repositorio

```bash
git clone <repository-url>
cd ERP
```

### 2. Configurar la Base de Datos

#### Crear la Base de Datos

Abre tu cliente PostgreSQL (pgAdmin, DBeaver, psql) y ejecuta:

```sql
CREATE DATABASE bd_erp;
```

#### Ejecutar el Esquema Inicial

Ejecuta el archivo SQL principal que contiene todas las sentencias `CREATE TABLE`.

#### Aplicar Actualizaciones del Esquema

Ejecuta las siguientes actualizaciones en orden:

```sql
-- 1. Añadir columna de saldo a favor en clientes
ALTER TABLE public.clientes
ADD COLUMN saldo_a_favor numeric(18, 2) NOT NULL DEFAULT 0.00;

-- 2. Cambiar el tipo de la columna logo_url en empresas
ALTER TABLE public.empresas
ALTER COLUMN logo_url TYPE TEXT;

-- 3. Convertir todas las llaves primarias a autoincrementables (IDENTITY)
DO $$
DECLARE
    rec RECORD;
BEGIN
    FOR rec IN
        SELECT tc.table_name, kcu.column_name
        FROM information_schema.table_constraints AS tc
        JOIN information_schema.key_column_usage AS kcu
          ON tc.constraint_name = kcu.constraint_name
        JOIN information_schema.columns AS c
          ON c.table_name = tc.table_name
          AND c.column_name = kcu.column_name
        WHERE tc.constraint_type = 'PRIMARY KEY'
          AND c.data_type = 'integer'
    LOOP
        EXECUTE format('ALTER TABLE public.%I ALTER COLUMN %I DROP DEFAULT;',
                      rec.table_name, rec.column_name);
        EXECUTE format('ALTER TABLE public.%I ALTER COLUMN %I ADD GENERATED BY DEFAULT AS IDENTITY;',
                      rec.table_name, rec.column_name);
    END LOOP;
END $$;
```

#### Insertar Datos Esenciales

Ejecuta el script SQL de datos maestros que incluye:
- Permisos del sistema
- Roles predeterminados
- Monedas (PEN, USD)
- Tipos de comprobante
- Plan de cuentas contable base

### 3. Instalar Dependencias del Backend

```bash
cd backend
npm install
```

### 4. Instalar Dependencias del Frontend

```bash
cd frontend
npm install
```

---

## ⚙️ Configuración

### Variables de Entorno del Backend

Crea un archivo `.env` en la carpeta `/backend`:

```env
# Puerto del servidor
PORT=4000

# Configuración de PostgreSQL
DB_USER=postgres
DB_HOST=localhost
DB_DATABASE=bd_erp
DB_PASSWORD=tu_contraseña_segura
DB_PORT=5432

# JWT Secret (usa una cadena aleatoria segura)
JWT_SECRET=tu_secreto_jwt_muy_seguro_cambiame
```

> **Importante**: Nunca compartas el archivo `.env` ni lo subas al repositorio. Está incluido en `.gitignore`.

### Configuración del Frontend

El frontend está configurado para conectarse a `http://localhost:4000` por defecto. Si necesitas cambiar esto, edita el archivo de configuración del servicio API.

---

## 💻 Uso

### Iniciar el Backend

```bash
cd backend
npm run dev
```

El servidor estará corriendo en **http://localhost:4000**

Deberías ver en consola:
```
✅ Conexión a la base de datos establecida exitosamente.
🚀 Servidor corriendo en http://localhost:4000
```

### Iniciar el Frontend

En una nueva terminal:

```bash
cd frontend
npm run dev
```

La aplicación estará disponible en **http://localhost:5173**

### Acceso al Sistema

1. Abre tu navegador en `http://localhost:5173`
2. Inicia sesión con las credenciales del usuario administrador creado en el script de datos iniciales
3. Comienza a usar el sistema

---

## 📁 Estructura del Proyecto

```
ERP/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── database.ts          # Configuración de PostgreSQL Pool
│   │   ├── controllers/             # Controladores HTTP
│   │   │   ├── auth.controller.ts
│   │   │   ├── venta.controller.ts
│   │   │   ├── compra.controller.ts
│   │   │   └── ...
│   │   ├── middleware/              # Middlewares Express
│   │   │   ├── auth.middleware.ts   # Verificación JWT
│   │   │   └── authorization.middleware.ts  # Permisos
│   │   ├── routes/                  # Definición de rutas
│   │   │   ├── auth.routes.ts
│   │   │   ├── venta.routes.ts
│   │   │   └── ...
│   │   ├── services/                # Lógica de negocio
│   │   │   ├── auth.service.ts
│   │   │   ├── venta.service.ts
│   │   │   ├── asientoContable.service.ts
│   │   │   ├── auditoria.service.ts
│   │   │   └── ...
│   │   ├── utils/                   # Utilidades
│   │   │   └── errors.ts
│   │   └── index.ts                 # Punto de entrada
│   ├── .env                         # Variables de entorno (no versionado)
│   ├── package.json
│   └── tsconfig.json
│
├── frontend/
│   ├── src/
│   │   ├── assets/                  # Imágenes, logos, etc.
│   │   ├── components/              # Componentes reutilizables
│   │   │   ├── common/              # Componentes comunes
│   │   │   └── layout/              # Layout components
│   │   ├── context/                 # React Context
│   │   │   └── AuthContext.tsx      # Contexto de autenticación
│   │   ├── hooks/                   # Custom hooks
│   │   │   └── useAuth.ts
│   │   ├── pages/                   # Páginas de la aplicación
│   │   │   ├── dashboard/
│   │   │   ├── clientes/
│   │   │   ├── ventas/
│   │   │   ├── compras/
│   │   │   ├── tesoreria/
│   │   │   ├── contabilidad/
│   │   │   ├── reportes/
│   │   │   └── configuracion/
│   │   ├── router/                  # Configuración de rutas
│   │   │   └── ProtectedRoute.tsx
│   │   ├── services/                # Servicios API
│   │   │   ├── authService.ts
│   │   │   ├── ventaService.ts
│   │   │   ├── notificationService.ts
│   │   │   └── ...
│   │   ├── styles/                  # Estilos CSS
│   │   ├── App.tsx                  # Componente raíz
│   │   ├── main.tsx                 # Punto de entrada
│   │   └── index.css
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.config.ts
│
└── README.md                        # Este archivo
```

---

## 🔌 API Endpoints

### Autenticación
```
POST   /api/auth/login              # Iniciar sesión
GET    /api/auth/profile            # Obtener perfil del usuario
```

### Ventas
```
GET    /api/ventas                  # Listar facturas de venta
POST   /api/ventas                  # Crear factura de venta
GET    /api/ventas/:id              # Obtener factura por ID
PUT    /api/ventas/:id              # Actualizar factura
DELETE /api/ventas/:id              # Anular factura
GET    /api/ventas/:id/download/pdf # Descargar PDF
GET    /api/ventas/:id/download/xml # Descargar XML
POST   /api/ventas/:id/aplicar-saldo # Aplicar saldo a favor
```

### Compras
```
GET    /api/compras                 # Listar facturas de compra
POST   /api/compras                 # Crear factura de compra
GET    /api/compras/:id             # Obtener factura por ID
PUT    /api/compras/:id             # Actualizar factura
DELETE /api/compras/:id             # Anular factura
```

### Contabilidad
```
GET    /api/plan-contable           # Obtener plan de cuentas
POST   /api/plan-contable           # Crear cuenta contable
GET    /api/asientos-contables      # Listar asientos contables
POST   /api/asientos-contables      # Crear asiento manual
```

### Reportes
```
GET    /api/reportes/ple-compras    # Libro electrónico de compras
GET    /api/reportes/ple-ventas     # Libro electrónico de ventas
GET    /api/reportes-contables/estado-resultados  # Estado de resultados
GET    /api/reportes-contables/balance-general    # Balance general
```

### Dashboard
```
GET    /api/dashboard/kpis          # KPIs del dashboard
GET    /api/dashboard/flujo-caja    # Flujo de caja
GET    /api/dashboard/rentabilidad  # Rentabilidad por cliente
```

> **Nota**: Todos los endpoints (excepto `/api/auth/login`) requieren autenticación mediante token JWT en el header `Authorization: Bearer <token>`.

---

## 🔐 Sistema de Permisos

El sistema utiliza un modelo de permisos basado en roles:

- **Usuarios** → pueden tener múltiples **Roles**
- **Roles** → contienen múltiples **Permisos**
- **Permisos** → definen acciones específicas (ej: `VER_FACTURAS_VENTA`, `CREAR_CLIENTES`)

### Implementación

**Backend** (middleware):
```typescript
router.post('/', verifyToken, checkPermission('CREAR_FACTURAS_VENTA'), createFactura);
```

**Frontend** (componente):
```typescript
{hasPermission('CREAR_FACTURAS_VENTA') && (
  <button onClick={handleCreate}>Nueva Venta</button>
)}
```

---

## 🎨 Características Técnicas Destacadas

### Generación Automática de Asientos Contables

Cada vez que se crea una venta o compra, el sistema automáticamente:
1. Identifica las cuentas contables apropiadas del plan de cuentas
2. Genera un asiento contable de doble partida
3. Registra el movimiento en el módulo de contabilidad
4. Actualiza los saldos de las cuentas afectadas

### Sistema de Auditoría

Todas las operaciones de creación, modificación y eliminación se registran automáticamente:
- **Usuario** que realizó la acción
- **Fecha y hora** exacta
- **Tabla afectada** y **ID del registro**
- **Valores anteriores y nuevos** (para modificaciones)
- **IP de origen** y **módulo del sistema**

### Multi-Empresa

El sistema soporta múltiples empresas en la misma base de datos:
- Cada usuario pertenece a una empresa específica
- Todas las consultas se filtran automáticamente por `empresa_id`
- Permite gestionar varias empresas desde una sola instalación

### Cumplimiento SUNAT

- Generación de XML según especificaciones UBL 2.1
- Formato de Libros Electrónicos PLE versión 5.0
- Cálculo automático de impuestos (IGV, ISC, otros)
- Numeración correlativa de comprobantes por serie

---

## 🛡 Seguridad

- ✅ Contraseñas hasheadas con bcrypt (10 rounds)
- ✅ Autenticación mediante JWT con expiración configurable
- ✅ Tokens renovables sin perder la sesión
- ✅ Validación de permisos en backend y frontend
- ✅ Protección CORS configurada
- ✅ Sanitización de inputs para prevenir SQL injection
- ✅ Headers de auditoría en todas las mutaciones
- ✅ Registro completo de acciones del sistema

---

## 📝 Comandos Útiles

### Backend

```bash
# Desarrollo con hot-reload
npm run dev

# Compilar TypeScript
npm run build

# Ejecutar versión compilada
npm start
```

### Frontend

```bash
# Desarrollo
npm run dev

# Build para producción
npm run build

# Preview del build de producción
npm run preview

# Linting
npm run lint
```

---

## 📄 Licencia

Este proyecto es propietario y confidencial. Todos los derechos reservados.

---

<div align="center">

**Desarrollado con usando TypeScript, React y Node.js**

</div>
