# 📦 Documentacion de Laboratorio #3 de Desarrollo de Software 7 - CRUD Rápido con Laravel

## 📌 Introducción

Este proyecto consiste en el desarrollo de un sistema CRUD (Create, Read, Update, Delete) para la gestión de productos utilizando **Laravel**, **MySQL**, **Bootstrap** y herramientas de automatización como **ibex/crud-generator**.

El laboratorio permite comprender la estructura MVC de Laravel, el manejo de migraciones, rutas, modelos, controladores, vistas y validaciones.

---

## 🎯 Objetivos

- Crear un proyecto Laravel desde cero.
- Configurar conexión con base de datos MySQL.
- Crear migraciones y modelos.
- Generar CRUD automático.
- Implementar vistas con Bootstrap.
- Gestionar productos mediante operaciones básicas.

---

## 🛠️ Tecnologías Utilizadas

- 🐘 PHP 8+
- 🚀 Laravel
- 🗄️ MySQL / phpMyAdmin
- 📦 Composer
- 🟢 Node.js / NPM
- 🖌️Bootstrap
- ⚙️ Vite

---

## 📂 Estructura del Proyecto

En la arquitectura MVC:

- **Modelos (Models):** Gestionan los datos y conexión con la base de datos.
- **Vistas (Views):** Interfaz gráfica del usuario.
- **Controladores (Controllers):** Conectan lógica entre vistas y modelos.

---

# 🚀 Instalación del Proyecto

## 1️⃣ Crear Proyecto Laravel

```bash
laravel new crud_rapido
cd crud_rapido
```

## 2️⃣ Configurar Variables de Entorno

Editar archivo .env

```bash
DB_DATABASE=crud_rapido
DB_USERNAME=root
DB_PASSWORD=
```

## 3️⃣ Solución Error Longitud de Cadena

Editar: app/Providers/AppServiceProvider.php

```bash
use Illuminate\Support\Facades\Schema;

public function boot(): void
{
    Schema::defaultStringLength(191);
}
```

## 4️⃣ Limpiar Configuración

```bash
php artisan config:clear
php artisan cache:clear
php artisan config:cache
```

# 🗄️ Base de Datos

## 1️⃣ Crear Modelo + Migración

```bash
php artisan make:model Product -m
```

## 2️⃣ Editar Migración

Archivo: database/migrations/create_products_table.php

```bash
$table->id();
$table->string('description');
$table->double('price',8,2);
$table->integer('stock');
$table->timestamps();
```

## 3️⃣ Ejecutar Migraciones

```bash
php artisan migrate
```

# 📦 Modelo Product

Archivo: app/Models/Product.php

```bash
protected $fillable = [
    'description',
    'price',
    'stock'
];
```

## 📌 Importancia de $fillable

Permite la asignación masiva segura de datos al crear o actualizar registros.

# ⚙️ Generación CRUD Automática

## 1️⃣ Instalar Generador

```bash
composer require ibex/crud-generator --dev
```

## 2️⃣ Publicar Recursos

```bash
php artisan vendor:publish --tag=crud
```

## 3️⃣ Crear CRUD

```bash
php artisan make:crud products
```

# 🛣️ Rutas

Archivo: routes/web.php

```bash
use App\Http\Controllers\ProductController;

Route::resource('products', ProductController::class);
```

## Rutas CRUD Generadas

table>
  <thead>
    <tr>
      <th>Método</th>
      <th>Ruta</th>
      <th>Acción</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>GET</td>
      <td>/products</td>
      <td>index</td>
    </tr>
    <tr>
      <td>GET</td>
      <td>/products/create</td>
      <td>create</td>
    </tr>
    <tr>
      <td>POST</td>
      <td>/products</td>
      <td>store</td>
    </tr>
    <tr>
      <td>GET</td>
      <td>/products/{id}</td>
      <td>show</td>
    </tr>
    <tr>
      <td>GET</td>
      <td>/products/{id}/edit</td>
      <td>edit</td>
    </tr>
    <tr>
      <td>PUT / PATCH</td>
      <td>/products/{id}</td>
      <td>update</td>
    </tr>
    <tr>
      <td>DELETE</td>
      <td>/products/{id}</td>
      <td>destroy</td>
    </tr>
  </tbody>
</table>
