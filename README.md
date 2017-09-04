# Tabla de contenidos
-  [Introducción](#introducción)
-  [API](#api-de-la-aplicación-Galería-de-Arte)
  - [Recurso Artista](#recurso-artista)
    - [GET /artistas](#GET-/artistas)
    - [GET /artista/{id}](#GET-/artista/{id})
    - [POST /artistas](#POST-/artistas)
    - [PUT /artistas/{id}](#PUT-/artistas/{id})
    - [DELETE /artistas/{id}](#DELETE-/artistas/{id})
    - [GET artistas/{id}/obras](#GET-artistas/{id}/obras)
    - [POST artistas/{id}/obras/{idObras}](#POST-artistas/{id}/obras/{idObras})
    - [PUT artistas/{id}/obras](#PUT-artistas/{id}/obras)
    - [DELETE artistas/{id}/obras/{idObras}](#DELETE-artistas/{id}/obras/{idObras}])
    - [GET artistas/{id}/blog](#GET-artistas/{id}/blog)
    - [GET artistas/{id}/blog/{idBlog}](#GET-artistas/{id}/blog/{idBlog})
    - [POST artistas/{id}/blog/{idBlog}](#POST-artistas/{id}/blog/{idBlog})
    - [PUT artistas/{id}/blog](#PUT-artistas/{id}/blog)
    - [DELETE artistas/{id}/blog/{idBlog}](#DELETE-artistas/{id}/blog/{idBlog}])
    - [GET artistas/{id}/comentario](#GET-artistas/{id}/comentario)
    - [GET artistas/{id}/comentario/{idComentario}](#GET-artistas/{id}/comentario/{idComentario})
    - [POST artistas/{id}/comentario/{idComentario}](#POST-artistas/{id}/comentario/{idComentario})
    - [PUT artistas/{id}/comentario](#PUT-artistas/{id}/comentario)
    - [DELETE artistas/{id}/comentario/{idComentario}](#DELETE-artistas/{id}/comentario/{idComentario}])
  - [Recurso Obra](#recurso-obra)
    - [GET /obra](#GET-/obra)
    - [GET /obra/{id}](#GET-/obra/{id})
    - [POST /obra](#POST-/obra)
    - [PUT /obra/{id}](#PUT-/obra/{id})
    - [DELETE /obra/{id}](#DELETE-/obra/{id})
    - [GET obra/{idObra}/precio](#GET-obra/{idObra}/precio)
    - [GET obra/{idObra}/precio/{precioObra}](#GET-obra/{idObra}/precio/{precioObra})
    - [POST obra/{idObra}/precio/{precioObra}](#POST-obra/{idObra}/precio/{precioObra})
    - [PUT obra/{idObra}/precio](#PUT-obra/{idObra}/precio)
    - [DELETE obra/{idObra}/precio/{precioObra}](#DELETE-obra/{idObra}/precio/{precioObra}])
    - [GET obra/{idObra}/artistas](#GET-obra/{idObra}/artistas)
    - [GET obra/{idObra}/artistas/{idArtista}](#GET-obra/{idObra}/artistas/{idArtista})
    - [POST obra/{idObra}/artistas/{idArtista}](#POST-obra/{idObra}/artistas/{idArtista})
    - [PUT obra/{idObra}/artistas](#PUT-obra/{idObra}/artistas)
    - [DELETE obra/{idObra}/artistas/{idArtista}](#DELETE-obra/{idObra}/artistas/{idArtista}])
  - [Recurso Editorial](#recurso-editorial)
    - [GET /editorials](#GET-/editorials)
    - [GET /editorials/{id}](#GET-/editorials/{id})
    - [POST /editorials](#POST-/editorials)
    - [PUT /editorials/{id}](#PUT-/editorials/{id})
    - [DELETE /editorials/{id}](#DELETE-/editorials/{id})
    - [GET editorials/{editorialsid}/editedbooks](#GET-editorials/{editorialsid}/editedbooks)
    - [GET editorials/{editorialsid}/editedbooks/{editedbooksid}](#GET-editorials/{editorialsid}/editedbooks/{editedbooksid})
    - [POST editorials/{editorialsid}/editedbooks/{editedbooksid}](#POST-editorials/{editorialsid}/editedbooks/{editedbooksid})
    - [PUT editorials/{editorialsid}/editedbooks](#PUT-editorials/{editorialsid}/editedbooks)
    - [DELETE editorials/{editorialsid}/editedbooks/{editedbooksid}](#DELETE-editorials/{editorialsid}/editedbooks/{editedbooksid}])
  - [Recurso Prize](#recurso-prize)
    - [GET /prizes](#GET-/prizes)
    - [GET /prizes/{id}](#GET-/prizes/{id})
    - [POST /prizes](#POST-/prizes)
    - [PUT /prizes/{id}](#PUT-/prizes/{id})
    - [DELETE /prizes/{id}](#DELETE-/prizes/{id})
  - [Recurso Category](#recurso-category)
    - [GET /categorys](#GET-/categorys)
    - [GET /categorys/{id}](#GET-/categorys/{id})
    - [POST /categorys](#POST-/categorys)
    - [PUT /categorys/{id}](#PUT-/categorys/{id})
    - [DELETE /categorys/{id}](#DELETE-/categorys/{id})
    - [GET categorys/{categorysid}/books](#GET-categorys/{categorysid}/books)
    - [GET categorys/{categorysid}/books/{booksid}](#GET-categorys/{categorysid}/books/{booksid})
    - [POST categorys/{categorysid}/books/{booksid}](#POST-categorys/{categorysid}/books/{booksid})
    - [PUT categorys/{categorysid}/books](#PUT-categorys/{categorysid}/books)
    - [DELETE categorys/{categorysid}/books/{booksid}](#DELETE-categorys/{categorysid}/books/{booksid}])

# API Rest
## Introducción
La comunicación entre cliente y servidor se realiza intercambiando objetos JSON. Para cada entidad se hace un mapeo a JSON, donde cada uno de sus atributos se transforma en una propiedad de un objeto JSON. Todos los servicios se generan en la URL /books_absviews.api/api/. Por defecto, todas las entidades tienen un atributo `id`, con el cual se identifica cada registro:

```javascript
{
    id: '',
    attribute_1: '',
    attribute_2: '',
    ...
    attribute_n: ''
}
```

Cuando se transmite información sobre un registro específico, se realiza enviando un objeto con la estructura mencionada en la sección anterior.
La única excepción se presenta al solicitar al servidor una lista de los registros en la base de datos, que incluye información adicional para manejar paginación de lado del servidor en el header `X-Total-Count` y los registros se envían en el cuerpo del mensaje como un arreglo.

La respuesta del servidor al solicitar una colección presenta el siguiente formato:

```javascript
[{}, {}, {}, {}, {}, {}]
```

## API de la aplicación Galeria_de_Arte
### Recurso Artista
El objeto Artista tiene 2 representaciones JSON:

#### Representación Minimum
```javascript
{
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/,
    hojaVida: '' /*Tipo String*/,
    trayectoria: '' /*Tipo String*/,
    
}
```

#### Representación Detail
```javascript
{
    // todo lo de la representación Minimum más los objetos Minimum con relación simple.
    obra: {
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/  
    tipo: '' /*Tipo String*/  
    valor: '' /*Tipo Double*/  
    cantidad: '' /*Tipo Integer*/  
}
}
```



#### GET /books

Retorna una colección de objetos Book en representación Detail.
Cada Book en la colección tiene embebidos los siguientes objetos: Editorial.

#### Parámetros

#### N/A

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de [representaciones Detail](#recurso-book)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### GET /books/{id}

Retorna una colección de objetos Book en representación Detail.
Cada Book en la colección tiene los siguientes objetos: Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Book en [representaciones Detail](#recurso-book)
404|No existe un objeto Book con el ID solicitado|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### POST /books

Es el encargado de crear objetos Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
body|body|Objeto Book que será creado|Sí|[Representación Detail](#recurso-book)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Book ha sido creado|[Representación Detail](#recurso-book)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo crear el objeto Book|Mensaje de error

#### PUT /books/{id}

Es el encargado de actualizar objetos Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a actualizar|Sí|Integer
body|body|Objeto Book nuevo|Sí|[Representación Detail](#recurso-book)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Book actualizado|[Representación Detail](#recurso-book)
412|business exception, no se cumple con las reglas de negocio|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo actualizar el objeto Book|Mensaje de error

#### DELETE /books/{id}

Elimina un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a eliminar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto eliminado|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET books/{booksid}/categories

Retorna una colección de objetos Category asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Category en [representación Detail](#recurso-category)
500|Error consultando categories |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET books/{booksid}/categories/{categoriesid}

Retorna un objeto Category asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book a consultar|Sí|Integer
categoriesid|Path|ID del objeto Category a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Category en [representación Detail](#recurso-category)
404|No existe un objeto Category con el ID solicitado asociado al objeto Book indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST books/{booksid}/categories/{categoriesid}

Asocia un objeto Category a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|PathParam|ID del objeto Book al cual se asociará el objeto Category|Sí|Integer
categoriesid|PathParam|ID del objeto Category a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Category asociado|[Representación Detail de Category](#recurso-category)
500|No se pudo asociar el objeto Category|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT books/{booksid}/categories

Es el encargado de remplazar la colección de objetos Category asociada a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Category|Sí|[Representación Detail](#recurso-category)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Category en [Representación Detail](#recurso-category)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE books/{booksid}/categories/{categoriesid}

Remueve un objeto Category de la colección en un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book asociado al objeto Category|Sí|Integer
categoriesid|Path|ID del objeto Category a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET books/{booksid}/authors

Retorna una colección de objetos Author asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Author en [representación Detail](#recurso-author)
500|Error consultando authors |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET books/{booksid}/authors/{authorsid}

Retorna un objeto Author asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book a consultar|Sí|Integer
authorsid|Path|ID del objeto Author a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Author en [representación Detail](#recurso-author)
404|No existe un objeto Author con el ID solicitado asociado al objeto Book indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST books/{booksid}/authors/{authorsid}

Asocia un objeto Author a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|PathParam|ID del objeto Book al cual se asociará el objeto Author|Sí|Integer
authorsid|PathParam|ID del objeto Author a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Author asociado|[Representación Detail de Author](#recurso-author)
500|No se pudo asociar el objeto Author|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT books/{booksid}/authors

Es el encargado de remplazar la colección de objetos Author asociada a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Author|Sí|[Representación Detail](#recurso-author)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Author en [Representación Detail](#recurso-author)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE books/{booksid}/authors/{authorsid}

Remueve un objeto Author de la colección en un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book asociado al objeto Author|Sí|Integer
authorsid|Path|ID del objeto Author a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error


#### GET books/{booksid}/review

Retorna una colección de objetos Review asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Review en [representación Detail](#recurso-review)
500|Error consultando review |Mensaje de error

#### GET books/{booksid}/review/{reviewid}

Retorna un objeto Review asociados a un objeto Book en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book a consultar|Sí|Integer
reviewid|Path|ID del objeto Review a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Review en [representación Detail](#recurso-review)
404|No existe un objeto Review con el ID solicitado asociado al objeto Book indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST books/{booksid}/review/{reviewid}

Asocia un objeto Review a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|PathParam|ID del objeto Book al cual se asociará el objeto Review|Sí|Integer
reviewid|PathParam|ID del objeto Review a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Review asociado|[Representación Detail de Review](#recurso-review)
500|No se pudo asociar el objeto Review|Mensaje de error

#### PUT books/{booksid}/review

Es el encargado de actualizar un objeto Review asociada a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Review|Sí|[Representación Detail](#recurso-review)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se actualizo el objeto|Objeto Review en [Representación Detail](#recurso-review)
500|No se pudo actualizar|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE books/{booksid}/review/{reviewid}

Remueve un objeto Review asociado a un objeto Book.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
booksid|Path|ID del objeto Book asociado al objeto Review|Sí|Integer
reviewid|Path|ID del objeto Review a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error


[Volver arriba](#tabla-de-contenidos)
### Recurso Author
El objeto Author tiene 2 representaciones JSON:

#### Representación Minimum
```javascript
{
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/,
    birthDate: '' /*Tipo Date*/
}
```




#### GET /authors

Retorna una colección de objetos Author en representación Detail.

#### Parámetros

#### N/A

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de [representaciones Detail](#recurso-author)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### GET /authors/{id}

Retorna una colección de objetos Author en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Author a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Author en [representaciones Detail](#recurso-author)
404|No existe un objeto Author con el ID solicitado|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### POST /authors

Es el encargado de crear objetos Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
body|body|Objeto Author que será creado|Sí|[Representación Detail](#recurso-author)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Author ha sido creado|[Representación Detail](#recurso-author)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo crear el objeto Author|Mensaje de error

#### PUT /authors/{id}

Es el encargado de actualizar objetos Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Author a actualizar|Sí|Integer
body|body|Objeto Author nuevo|Sí|[Representación Detail](#recurso-author)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Author actualizado|[Representación Detail](#recurso-author)
412|business exception, no se cumple con las reglas de negocio|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo actualizar el objeto Author|Mensaje de error

#### DELETE /authors/{id}

Elimina un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Author a eliminar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto eliminado|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET authors/{authorsid}/prize

Retorna una colección de objetos Prize asociados a un objeto Author en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Author a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Prize en [representación Detail](#recurso-prize)
500|Error consultando prize |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET authors/{authorsid}/prize/{prizeid}

Retorna un objeto Prize asociados a un objeto Author en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author a consultar|Sí|Integer
prizeid|Path|ID del objeto Prize a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Prize en [representación Detail](#recurso-prize)
404|No existe un objeto Prize con el ID solicitado asociado al objeto Author indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST authors/{authorsid}/prize/{prizeid}

Asocia un objeto Prize a un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|PathParam|ID del objeto Author al cual se asociará el objeto Prize|Sí|Integer
prizeid|PathParam|ID del objeto Prize a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Prize asociado|[Representación Detail de Prize](#recurso-prize)
500|No se pudo asociar el objeto Prize|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT authors/{authorsid}/prize

Es el encargado de remplazar la colección de objetos Prize asociada a un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Prize|Sí|[Representación Detail](#recurso-prize)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Prize en [Representación Detail](#recurso-prize)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE authors/{authorsid}/prize/{prizeid}

Remueve un objeto Prize de la colección en un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author asociado al objeto Prize|Sí|Integer
prizeid|Path|ID del objeto Prize a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET authors/{authorsid}/books

Retorna una colección de objetos Book asociados a un objeto Author en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Author a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Book en [representación Detail](#recurso-book)
500|Error consultando books |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET authors/{authorsid}/books/{booksid}

Retorna un objeto Book asociados a un objeto Author en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author a consultar|Sí|Integer
booksid|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Book en [representación Detail](#recurso-book)
404|No existe un objeto Book con el ID solicitado asociado al objeto Author indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST authors/{authorsid}/books/{booksid}

Asocia un objeto Book a un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|PathParam|ID del objeto Author al cual se asociará el objeto Book|Sí|Integer
booksid|PathParam|ID del objeto Book a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Book asociado|[Representación Detail de Book](#recurso-book)
500|No se pudo asociar el objeto Book|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT authors/{authorsid}/books

Es el encargado de remplazar la colección de objetos Book asociada a un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Book|Sí|[Representación Detail](#recurso-book)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Book en [Representación Detail](#recurso-book)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE authors/{authorsid}/books/{booksid}

Remueve un objeto Book de la colección en un objeto Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
authorsid|Path|ID del objeto Author asociado al objeto Book|Sí|Integer
booksid|Path|ID del objeto Book a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error



[Volver arriba](#tabla-de-contenidos)
### Recurso Editorial
El objeto Editorial tiene 2 representaciones JSON:

#### Representación Minimum
```javascript
{
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/
}
```




#### GET /editorials

Retorna una colección de objetos Editorial en representación Detail.

#### Parámetros

#### N/A

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de [representaciones Detail](#recurso-editorial)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### GET /editorials/{id}

Retorna una colección de objetos Editorial en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Editorial a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Editorial en [representaciones Detail](#recurso-editorial)
404|No existe un objeto Editorial con el ID solicitado|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### POST /editorials

Es el encargado de crear objetos Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
body|body|Objeto Editorial que será creado|Sí|[Representación Detail](#recurso-editorial)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Editorial ha sido creado|[Representación Detail](#recurso-editorial)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo crear el objeto Editorial|Mensaje de error

#### PUT /editorials/{id}

Es el encargado de actualizar objetos Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Editorial a actualizar|Sí|Integer
body|body|Objeto Editorial nuevo|Sí|[Representación Detail](#recurso-editorial)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Editorial actualizado|[Representación Detail](#recurso-editorial)
412|business exception, no se cumple con las reglas de negocio|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo actualizar el objeto Editorial|Mensaje de error

#### DELETE /editorials/{id}

Elimina un objeto Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Editorial a eliminar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto eliminado|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET editorials/{editorialsid}/editedbooks

Retorna una colección de objetos Book asociados a un objeto Editorial en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Editorial a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Book en [representación Detail](#recurso-book)
500|Error consultando editedbooks |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET editorials/{editorialsid}/editedbooks/{editedbooksid}

Retorna un objeto Book asociados a un objeto Editorial en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
editorialsid|Path|ID del objeto Editorial a consultar|Sí|Integer
editedbooksid|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Book en [representación Detail](#recurso-book)
404|No existe un objeto Book con el ID solicitado asociado al objeto Editorial indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST editorials/{editorialsid}/editedbooks/{editedbooksid}

Asocia un objeto Book a un objeto Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
editorialsid|PathParam|ID del objeto Editorial al cual se asociará el objeto Book|Sí|Integer
editedbooksid|PathParam|ID del objeto Book a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Book asociado|[Representación Detail de Book](#recurso-book)
500|No se pudo asociar el objeto Book|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT editorials/{editorialsid}/editedbooks

Es el encargado de remplazar la colección de objetos Book asociada a un objeto Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
editorialsid|Path|ID del objeto Editorial cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Book|Sí|[Representación Detail](#recurso-book)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Book en [Representación Detail](#recurso-book)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE editorials/{editorialsid}/editedbooks/{editedbooksid}

Remueve un objeto Book de la colección en un objeto Editorial.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
editorialsid|Path|ID del objeto Editorial asociado al objeto Book|Sí|Integer
editedbooksid|Path|ID del objeto Book a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error



[Volver arriba](#tabla-de-contenidos)
### Recurso Prize
El objeto Prize tiene 2 representaciones JSON:

#### Representación Minimum
```javascript
{
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/,
    datePrize: '' /*Tipo Date*/
}
```

#### Representación Detail
```javascript
{
    // todo lo de la representación Minimum más los objetos Minimum con relación simple.
    author: {
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/,
    birthDate: '' /*Tipo Date*/    }
}
```



#### GET /prizes

Retorna una colección de objetos Prize en representación Detail.
Cada Prize en la colección tiene embebidos los siguientes objetos: Author.

#### Parámetros

#### N/A

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de [representaciones Detail](#recurso-prize)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### GET /prizes/{id}

Retorna una colección de objetos Prize en representación Detail.
Cada Prize en la colección tiene los siguientes objetos: Author.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Prize a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Prize en [representaciones Detail](#recurso-prize)
404|No existe un objeto Prize con el ID solicitado|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### POST /prizes

Es el encargado de crear objetos Prize.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
body|body|Objeto Prize que será creado|Sí|[Representación Detail](#recurso-prize)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Prize ha sido creado|[Representación Detail](#recurso-prize)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo crear el objeto Prize|Mensaje de error

#### PUT /prizes/{id}

Es el encargado de actualizar objetos Prize.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Prize a actualizar|Sí|Integer
body|body|Objeto Prize nuevo|Sí|[Representación Detail](#recurso-prize)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Prize actualizado|[Representación Detail](#recurso-prize)
412|business exception, no se cumple con las reglas de negocio|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo actualizar el objeto Prize|Mensaje de error

#### DELETE /prizes/{id}

Elimina un objeto Prize.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Prize a eliminar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto eliminado|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error



[Volver arriba](#tabla-de-contenidos)
### Recurso Category
El objeto Category tiene 2 representaciones JSON:

#### Representación Minimum
```javascript
{
    id: '' /*Tipo Long*/,
    name: '' /*Tipo String*/
}
```




#### GET /categorys

Retorna una colección de objetos Category en representación Detail.

#### Parámetros

#### N/A

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de [representaciones Detail](#recurso-category)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### GET /categorys/{id}

Retorna una colección de objetos Category en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Category a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Category en [representaciones Detail](#recurso-category)
404|No existe un objeto Category con el ID solicitado|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|Error interno|Mensaje de error

#### POST /categorys

Es el encargado de crear objetos Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
body|body|Objeto Category que será creado|Sí|[Representación Detail](#recurso-category)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Category ha sido creado|[Representación Detail](#recurso-category)
412|precondition failed, no se cumple la regla de negocio establecida|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo crear el objeto Category|Mensaje de error

#### PUT /categorys/{id}

Es el encargado de actualizar objetos Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Category a actualizar|Sí|Integer
body|body|Objeto Category nuevo|Sí|[Representación Detail](#recurso-category)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
201|El objeto Category actualizado|[Representación Detail](#recurso-category)
412|business exception, no se cumple con las reglas de negocio|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error
500|No se pudo actualizar el objeto Category|Mensaje de error

#### DELETE /categorys/{id}

Elimina un objeto Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Category a eliminar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto eliminado|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET categorys/{categorysid}/books

Retorna una colección de objetos Book asociados a un objeto Category en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
id|Path|ID del objeto Category a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Colección de objetos Book en [representación Detail](#recurso-book)
500|Error consultando books |Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### GET categorys/{categorysid}/books/{booksid}

Retorna un objeto Book asociados a un objeto Category en representación Detail.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
categorysid|Path|ID del objeto Category a consultar|Sí|Integer
booksid|Path|ID del objeto Book a consultar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|OK|Objeto Book en [representación Detail](#recurso-book)
404|No existe un objeto Book con el ID solicitado asociado al objeto Category indicado |Mensaje de error
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### POST categorys/{categorysid}/books/{booksid}

Asocia un objeto Book a un objeto Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
categorysid|PathParam|ID del objeto Category al cual se asociará el objeto Book|Sí|Integer
booksid|PathParam|ID del objeto Book a asociar|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Objeto Book asociado|[Representación Detail de Book](#recurso-book)
500|No se pudo asociar el objeto Book|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### PUT categorys/{categorysid}/books

Es el encargado de remplazar la colección de objetos Book asociada a un objeto Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
categorysid|Path|ID del objeto Category cuya colección será remplazada|Sí|Integer
body|body|Colección de objetos Book|Sí|[Representación Detail](#recurso-book)

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
200|Se remplazó la colección|Colección de objetos Book en [Representación Detail](#recurso-book)
500|No se pudo remplazar la colección|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error

#### DELETE categorys/{categorysid}/books/{booksid}

Remueve un objeto Book de la colección en un objeto Category.

#### Parámetros

Nombre|Ubicación|Descripción|Requerido|Esquema
:--|:--|:--|:--|:--
categorysid|Path|ID del objeto Category asociado al objeto Book|Sí|Integer
booksid|Path|ID del objeto Book a remover|Sí|Integer

#### Respuesta

Código|Descripción|Cuerpo
:--|:--|:--
204|Objeto removido|N/A
500|Error interno|Mensaje de error
405|method not allowed, no existe permiso para el recurso|Mensaje de error



[Volver arriba](#tabla-de-contenidos)
