## Versión 1: planificación y configuración inicial

> Creamos un controlador con los metodos de una api con el comando `--api`

```
php artisan make:controller Api/V1/PostController --api --model=Post

```

> Para la cracion de las rutas nos dirigimos a `routes\api.php`, y creamos las rutas, en este caso podemos emplear la ruta tipo apiResource

```
Route::apiResource('v1/posts',PostController::class);


```

> el metodo `->only('[nombre de la ruta]');` permite emplear unicamentela ruta que estamos definiendo en el only

## Versión 1: recurso

Dar formato al recurso, vamos a crear una nueva clase para lograr el objetivo, por lo tanto en la terminal escribimos:

```
php artisan make:resource V1/PostResource

```

Esto crea un recurso en la carpeta de recursos `app\Http\Resources\V1\PostResource.php`

> En esta clase modificamos el metodo `toArray()` para que retorne un array con los datos deseados

```
public function toArray($request)
    {
        return [
            'title'=>$this->title,
            'slug'=>$this->slug,
            'excerpt' => $this->excerpt,
            'content' => $this->content
        ];
    }
```
>Despues en el controlador `app\Http\Controllers\Api\V1\PostController.php` impleentamos esta nueva clase.
```
  public function show(Post $post)
    {
        return new PostResource($post);
    }
```
>Enviamos el post consultado a la clase resouce y el metodo show retorna el post formateado