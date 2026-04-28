# 📦 Documentacion de Laboratorio #3 de Desarrollo de Software 7 - CRUD Rápido con Laravel

---

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

---

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

---

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

---

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

---

# 🛣️ Rutas

Archivo: routes/web.php

```bash
use App\Http\Controllers\ProductController;

Route::resource('products', ProductController::class);
```

## Rutas CRUD Generadas

| Método     | Ruta                | Acción   |
| ---------- | ------------------- | -------- |
| GET        | /products           | index    |
| GET        | /products/create    | create   |
| POST       | /products           | store    |
| GET        | /products/{id}      | show     |
| GET        | /products/{id}/edit | edit     |
| PUT/PATCH  | /products/{id}      | update   |
| DELETE     | /products/{id}      | destroy  |

---

# 🎨 Interfaz Gráfica

## Instalar Laravel UI + Bootstrap

```bash
composer require laravel/ui --dev
php artisan ui bootstrap --auth
npm install
npm run dev
```

---

# ▶️ Ejecutar Proyecto

```bash
php artisan serve
```

Servidor: http://127.0.0.1:8000
CRUD Productos: http://127.0.0.1:8000/products

# 🧪 Funcionalidades

✅ Crear productos <br>
✅ Listar productos <br>
✅ Editar productos <br>
✅ Eliminar productos <br>
✅ Validación de formularios <br>
✅ Diseño Bootstrap <br>

---

# 🖼️ Capturas de Ejecución

## Pantalla de la Tabla de Productos

![image alt](https://github.com/OrlandoValdes/Lab_3---DS7/blob/master/Capturas/Pantalla_TablaProductos.png?raw=true)

## Pantalla de Creación de Producto

![image alt](https://github.com/OrlandoValdes/Lab_3---DS7/blob/master/Capturas/Pantalla_CrearProducto.png?raw=true)

## Pantalla de Enseñar Producto

![image alt](https://github.com/OrlandoValdes/Lab_3---DS7/blob/master/Capturas/Pantalla_Ense%C3%B1arProducto.png?raw=true)

## Pantalla de Actualizar Producto

![image alt](https://github.com/OrlandoValdes/Lab_3---DS7/blob/master/Capturas/Pantalla_ActualizarProducto.png?raw=true)

## Pantalla de Eliminar Producto

![image alt](https://github.com/OrlandoValdes/Lab_3---DS7/blob/master/Capturas/Pantalla_EliminarProducto.png?raw=true)

--- 

# ⚠️ Problemas Frecuentes

## Vite no reconocido

```bash
npm install
npm run dev
```

## Tabla ya existe

```bash
php artisan migrate:fresh
```

## ProductRequest no existe

```bash
php artisan make:request ProductRequest
```

## No guarda datos

Agregar:

```bash
protected $fillable = [...]
```

---

# 📚 Comandos Útiles

```bash
php artisan route:list
php artisan migrate
php artisan migrate:fresh
php artisan migrate:rollback
composer dump-autoload
npm run dev
```

# 📜 Referencias

1. Laravel. (2026). *Official Laravel Documentation*. https://laravel.com/docs
2. Laravel. (2026). *Database: Migrations*. https://laravel.com/docs/migrations
3. Bootstrap Team. (2026). *Bootstrap Official Documentation*. https://getbootstrap.com/docs/
4. Composer. (2026). *Composer Documentation*. https://getcomposer.org/doc/

---

#⏱️Fecha de Ejecución del Laboratorio

Sabado 25 de abril de 2026

-- 

<p align="center">
Este laboratorio ha sido desarrollado por el estudiante de la Universidad 
Tecnológica de Panamá: <br>
Nombre: Orlando Antonio Valdés Bernal<br>
Correo: orlando.valdes2@utp.ac.pa<br>
Curso: Desarrollo de Software 7 - 1GS131<br>
Instructor del Laboratorio: Irina Fong.
</p>


