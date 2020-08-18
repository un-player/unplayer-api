# unplayer-api

**Documentación e información de la API de UN Player**

## Generar API Keys

Visita el siguiente enlace con tu cuenta de UN Player para generar el acceso: [Generar API Keys](https://unplayer.com/settings/keys)

## API Endpoint

La API se encuentra en: `https://unplayer.com/api/1.0/` y se consume como RESTful.

## Uso de credenciales

**Método headers HTTP**

Puedes usar el header `Autorization` con el `API KEY` y `API PRIVATE` para authenticar. [Más información](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization).

**Método GET o POST params**

Puedes usar los parámetros `__api_key` para el **KEY** y  `__api_private` para el **PRIVATE**.

## Rate-limiting

Todos los métodos tienen un límite de 60 solicitudes por minuto. En caso de necesitar más por tu aplicación envianos un mensaje a contacto@unplayer.com explicando la razón para incrementar este límite para analizar tu aplicación.

## Métodos RESTful disponibles

**`GET user`**

**Descripción**
Obtener información de un usuario mediante cualquier ID de un servicio, así como los servicios asociados o disponibles.

Recomendamos guardar esta ID para luego re-usarla, esta ID nunca cambia y es única para identificar la cuenta en todos los servicios (SAMP, GTA V, Foro, Discord, TS, etc).

**Parámetros:**
```
type: enum("user", "samp", "gtav", "forum", "discord")
user_id: integer
```

**Respuesta:**
{
    "action": "GET 1.0\/user",
    "error": false,
    "ids": {
        "user": 12345,
        "forum": 12345,
        "gtav": 12345,
        "discord": "1234567890123457"
    }
}
***

**`GET gtav/user/{gtav_id}`**

**Descripción**
Obtener información básica del usuario GTA V

**Respuesta:**
```
{
    "action": "GET 1.0\/gtav\/user\/1",
    "name": "Nombre_Apellido",
    "level": 10,
    "banned": false,
    "played_time": 12456,
    "certification": 0
}
```

***

