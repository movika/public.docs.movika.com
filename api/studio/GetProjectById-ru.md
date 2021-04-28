---
title: GetProjectById
description: GetProjectById
keywords: GetProjectById
sort: 0
---

# GetProjectById

## Получить проект 

GET /{projectId}

Получить проект возможно по идентификатору, либо автору, либо пользователю с расширенными правами.


## Параметры запроса

## 1 Параметр пути

| header | type | format |
|---|---|---|
| projectId | integer | int64 |

## 12 Headers

| header | type | default | description |
|---|---|---|---|
| Authorization | string | Bearer {{accessToken}} | Токен пользователя с приставкой “Bearer |
| Accept-Charset | string | UTF-8 | Передача кодировки клиента | 
| Api-Version | string | {{apiVersion}} | Версия API | 
| App-Version | string | {{appVersion}} | Версия приложения клиента | 
| App-Name | string | {{appName}} | Наименование (Bundle ID) приложения | 
| Content-Type | string | application/json; charset=utf-8 | Тип содержимого | 
| Device-Id | string | {{deviceId}} | Идентификатор устройства, если имеется | 
| Accept-Language | string | {{acceptLanguage}} | Передача языка интерфейса клиента по стандарту 639-1 | 
| Session-Id | string | {{sessionId}} | Идентификатор сессии, формируется при запуске на устройстве клиента | 
| Api-Key | string | {{apikey}} | 

| header | type | enum |
|---|---|---|
| App-Environment | integer | ["0 - prod, 1 - dev, 2 - test/stage"] |


## Ответы сервера

## Ответ 200

Schema

Object
Cover, manifestUrl и Screens обязательные поля дял проектов со статусом DONE, в остальных случаях нет.
```
{
  "type": "object",
  "description": "Cover, manifestUrl и Screens обязательные поля дял проектов со статусом DONE, в остальных случаях нет.",
  "properties": {
    "id": {
      "type": "integer",
      "format": "int64"
    },
    "title": {
      "type": "string"
    },
    "cover": {
      "type": "string",
      "format": "uri"
    },
    "duration": {
      "type": "integer",
      "format": "int64"
    },
    "manifestUrl": {
      "type": "string",
      "format": "uri"
    },
    "author": {
      "type": "object",
      "required": [
        "id",
        "login"
      ],
      "properties": {
        "id": {
          "type": "integer",
          "format": "int64"
        },
        "firstName": {
          "type": "string"
        },
        "lastName": {
          "type": "string"
        },
        "avatarUri": {
          "type": "string",
          "format": "uri"
        },
        "login": {
          "type": "string"
        }
      }
    },
    "projectName": {
      "type": "string"
    },
    "status": {
      "type": "integer",
      "enum": [
        "0: IN_PROCCESS",
        "1:DONE",
        "2:ERROR",
        "3:TO_DEPLOY"
      ]
    },
    "projectType": {
      "type": "integer",
      "enum": [
        "1:Pro",
        "2:LiteEditor"
      ]
    },
    "keywords": {
      "type": "string"
    },
    "linkOnly": {
      "type": "boolean",
      "default": false
    },
    "createTime": {
      "type": "string",
      "format": "date-time"
    },
    "updateTime": {
      "type": "string",
      "format": "date-time"
    }
  },
  "required": [
    "id",
    "title",
    "duration",
    "author",
    "projectName",
    "createTime",
    "updateTime"
  ]
}
```

## Ответ 400
The 400 response.

## Ответ 401
Для доступа к запрашиваемому ресурсу требуется аутентификация.

1 Example

```
{
  "code": "sunt consequat proident",
  "status": -90024489,
  "timestamp": "1957-09-23T19:25:14.144Z",
  "error": "",
  "exception": "ut anim veniam dolor id",
  "message": "anim",
  "path": "ut dolore anim ",
  "stackTrace": "dol"
}
```
Schema
```
{
  "type": "object",
  "properties": {
    "code": {
      "type": "string",
      "description": "Код ошибки"
    },
    "error": {
      "type": "string",
      "description": "Расшифровка кода ошибки (code)"
    },
    "exception": {
      "type": "string",
      "description": "Название исключения"
    },
    "message": {
      "type": "string",
      "description": "Сообщение для пользователя"
    },
    "path": {
      "type": "string",
      "description": "Путь до ошибки"
    },
    "status": {
      "type": "integer",
      "description": "Статус код"
    },
    "timestamp": {
      "type": "string",
      "description": "Время исключения",
      "format": "date-time"
    },
    "stackTrace": {
      "type": "string"
    }
  },
  "required": [
    "code",
    "status",
    "timestamp"
  ]
}
```

## Ответ 404
The 404 response.

## Ответ 500
The 500 response.