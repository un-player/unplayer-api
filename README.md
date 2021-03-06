# unplayer-api

**Documentación e información de la API de UN Player**

## Uso de la API

**[Leer uso](https://github.com/un-player/unplayer-api/blob/master/USO.md)**

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
Obtener información básica del usuario.

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

***

**`GET gtav/org/{org_id}`**

**Descripción**
Obtener información de una ORG

**Respuesta:**
```
{
    "action": "GET 1.0\/gtav\/org\/20",
    "id": 20,
    "name": "Gobierno de San Andreas",
    "members_count": 30,
    "category": {
        "id": 11,
        "name": "Gubernamental",
        "certification": 1
    },
    "members": [
        {
            "name": "Nahuel_Sobredo",
            "user_id": 113,
            "rank_id": 55,
            "idx": 0
        },
        {
            "name": "Jose_Rey",
            "user_id": 3503,
            "rank_id": 56,
            "idx": 1
        },
        {
            "name": "David_Page",
            "user_id": 3706,
            "rank_id": 56,
            "idx": 1
        }
    ],
    "ranks": [
        {
            "id": 55,
            "name": "Alcalde",
            "idx": "0"
        },
        {
            "id": 392,
            "name": "Concejal",
            "idx": "7"
        },
        {
            "id": 393,
            "name": "Asistente",
            "idx": "8"
        }
    ]
}
```

## Métodos RESTful disponibles: SAMP

**`GET samp/user/{samp_id}`**

**Descripción**
Obtener información básica del usuario.

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
    ]
}
```

***

**`GET samp/org/{org_id}`**

**Descripción**
Obtener información de una ORG.

**Respuesta:**
```
{
    "action": "GET 1.0\/samp\/org\/1150",
    "id": 1150,
    "name": "Taller River Plate",
    "certification": 0,
    "members_count": 29,
    "members": [
        {
            "name": "Frank_Lindermann",
            "user_id": 24700,
            "rank_id": 906,
            "idx": 3
        },
        {
            "name": "Katrina_Rowling",
            "user_id": 26875,
            "rank_id": 905,
            "idx": 2
        }
    ],
    "ranks": [
        {
            "id": 904,
            "name": "Mister",
            "idx": "1"
        },
        {
            "id": 905,
            "name": "Gerente",
            "idx": "2"
        },
        {
            "id": 906,
            "name": "Supervisor",
            "idx": "3"
        },
        {
            "id": 907,
            "name": "Mec\u00e1nico Senior",
            "idx": "1907"
        },
        {
            "id": 911,
            "name": "M\u00e9canico Junior",
            "idx": "1911"
        }
    ]
}
```

***

**`GET samp/faction/{faction_id}`**

**Descripción**
Obtener información de una facción.

**Respuesta:**
```
{
    "action": "GET 1.0\/samp\/faction\/1",
    "id": 1,
    "name": "Gobierno",
    "members_count": 51,
    "members": [
        {
            "name": "Agustin_B\u00e1ez",
            "user_id": 57273,
            "rank_id": 1,
            "idx": 0
        },
        {
            "name": "Katrina_Rowling",
            "user_id": 26875,
            "rank_id": 2,
            "idx": 1
        }
    ],
    "ranks": [
        {
            "id": 1,
            "name": "Presidente",
            "idx": "0"
        },
        {
            "id": 2,
            "name": "Ministro(a)",
            "idx": "1"
        },
        {
            "id": 3,
            "name": "Agente",
            "idx": "2"
        },
        {
            "id": 4,
            "name": "Bur\u00f3crata",
            "idx": "3"
        },
        {
            "id": 5,
            "name": "Asistente",
            "idx": "4"
        }
    ]
}
```

