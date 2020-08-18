# unplayer-api

**Documentación e información de la API de UN Player**

## Uso de la API

**[Leer uso](https://github.com/un-player/unplayer-api/blob/master/README.md)**

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
```
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
```

## Métodos RESTful disponibles: GTAV

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
    "certification": 0,
    "orgs": [
        {
            "org_id": 89,
            "rank_id": 341,
            "idx": 0
        },
        {
            "org_id": 26,
            "rank_id": 75,
            "idx": 0
        },
        {
            "org_id": 21,
            "rank_id": 58,
            "idx": 0
        }
    ]
}
```

## Métodos RESTful disponibles: SAMP

**`GET samp/user/{samp_id}`**

**Descripción**
Obtener información básica del usuario GTA V

**Respuesta:**
```
{
    "action": "GET 1.0\/samp\/user\/1",
    "name": "Nombre_Apellido",
    "level": 10,
    "banned": false,
    "played_time": 12456,
    "certification": 0,
    "faction_id": 0,
    "faction_rank": 0,
    "orgs": [
        {
            "org_id": 1148,
            "rank_id": 884,
            "idx": 1
        }
    ],
}
```

***

