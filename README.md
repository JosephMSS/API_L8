## Versión 1: planificación y configuración inicial
> Creamos un controlador con los metodos de una api con el comando `--api`
```
php artisan make:controller Api/V1/PostController --api --model=Post

```
>Para la cracion de las rutas nos dirigimos a `routes\api.php`, y creamos las rutas, en este caso podemos emplear la ruta tipo apiResource
```
Route::apiResource('v1/posts',PostController::class);


```
> el metodo `->only('[nombre de la ruta]');` permite emplear unicamentela ruta que estamos definiendo en el only