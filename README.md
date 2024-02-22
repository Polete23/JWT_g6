# Json Web Tpken Grup 6
Enunciado actividad + proyecto iniciado
ENUNCIADO

Crear en laravel métodos de registro/login/get-user usando jwt. (opcional) Realizarlo con vue/nuxt.

REQUERIMIENTOS

LARAVEL
Paquete:
composer require tymon/jwt-auth:dev-develop --prefer-source

App/config.php (Providers)
Tymon\JWTAuth\Providers\LaravelServiceProvider::class,

App/config.php (Facades)
'JWTAuth' => Tymon\JWTAuth\Facades\JWTAuth::class, 
'JWTFactory' => Tymon\JWTAuth\Facades\JWTFactory::class,

Publicar configuracion:
php artisan vendor:publish --provider="Tymon\JWTAuth\Providers\LaravelServiceProvider"

Comprobar instalacion:
php artisan jwt:secret 
jwt-auth secret [0mrOWC8Xc6prYU148JZiJlRFotMuOrFsjNzr7mOEgZPFrA3LbItpb4FoYFaAc6Iz] set successfully.

Crear middleware de jwt:
php artisan make:middleware JwtMiddleware

Kernel.php:
protected $routeMiddleware = [
        'jwt.verify' => \App\Http\Middleware\JwtMiddleware::class,
];

Routes/api.php:
Route::group(['middleware' => ['jwt.verify']], function() {
       /*AÑADE AQUÍ LAS RUTAS QUE QUIERAS PROTEGER CON JWT*/
 });
