<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Laravel Sanctum API Project

This is a simple Laravel project set up with Sanctum for API authentication.

## Scaffolding

```bash
composer create-project laravel/laravel .
composer require laravel/ui
php artisan ui bootstrap --auth
npm install
npm run dev
php artisan serve
php artisan migrate --seed
http://127.0.0.1:8000/
```

## Sanctum

```bash
php artisan install:api
```

## Auth

app/Http/Controllers/Api/AuthController.php
```bash
php artisan make:controller Api/AuthController
```

use HasApiTokens at app/Models/User.php
```bash
use Laravel\Sanctum\HasApiTokens;

class User extends Authenticatable
{
    use HasApiTokens, Notifiable;
}
```
add api routes at routes/api.php
```bash
Route::post('register', [AuthController::class, 'register']);
Route::post('login', [AuthController::class, 'login']);
Route::post('logout', [AuthController::class, 'logout'])->middleware('auth:sanctum');
```

## Auth Postman

registration url: 
```bash
http://127.0.0.1:8000/api/register
```
Headers: 
```bash
Key:Accept Value:application/json
```
Body raw JSON
```bash
{
    "name": "Laz",
    "email": "laz@gmail.com",
    "password": "12345678",
    "password_confirmation": "12345678"
}
```
![Dashboard Screenshot](public/assets/images/screenshots/api_registration.png)

login url: 
```bash
http://127.0.0.1:8000/api/login
```
Headers: 
```bash
Key:Accept Value:application/json
```
Body raw JSON
```bash
{
    "email": "laz@gmail.com",
    "password": "12345678",
}
```
![Dashboard Screenshot](public/assets/images/screenshots/api_login.png)

postman: http://127.0.0.1:8000/api/logout
Headers: Key:Accept Value:application/json
Authorization: Bearer Token
![Dashboard Screenshot](public/assets/images/screenshots/api_logout.png)

### 5. Post

```bash
php artisan make:model Post -mfs
```
### 6. Policy

```bash
php artisan make:policy PostPolicy --model=Post
```
