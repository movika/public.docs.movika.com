---
title: Получить проект
description: Получить проект
keywords: Получить проект
sort: 0
---
 
# Получить проект 

## GetProjectById

GET /{projectId}

Получить проект возможно по идентификатору, либо автору, либо пользователю с расширенными правами.


## Параметры запроса

## 1 Параметр пути

| Path param | type | format |
|---|---|---|
| projectId | integer | int64 |

## 12 Headers

| header | type | default | description |
|---|---|---|---|
| Authorization | string | Bearer {{accessToken}} | Токен пользователя с приставкой “Bearer |
| Api-Version | string | {{apiVersion}} | Версия API | 
| Api-Key | string | {{apikey}} | 


## Ответы сервера

## Ответ 200

Schema

Object
Cover, manifestUrl и Screens обязательные поля для проектов со статусом DONE, в остальных случаях нет.
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
```
{
    "timestamp": "yyyy-MM-dd'T'HH:mm:ss'Z'",
    "path": "/error/some/path",
    "message": "exception message",
    "service": "exception_service_name",
    "code": unique_code (int),
    "status": 400
    "error": "error_name"
}
```

## Ответ 401
Для доступа к запрашиваемому ресурсу требуется аутентификация.

1 Example

```
{
    "timestamp": "yyyy-MM-dd'T'HH:mm:ss'Z'",
    "path": "/error/some/path",
    "message": "exception message",
    "service": "studio",
    "code": unique_code (int),
    "status": 401
    "error": "error_name"
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

## Ответ 403
```
{    
  "timestamp": "yyyy-MM-dd'T'HH:mm:ss'Z'",
    "path": "/error/some/path",
    "message": "exception message",
    "service": "studio",
    "code": unique_code (int),
    "status": 403
    "error": "error_name"
  }
```


## Ответ 404
```
{
    "timestamp": "yyyy-MM-dd'T'HH:mm:ss'Z'",
    "path": "/error/some/path",
    "message": "exception message",
    "service": "studio",
    "code": unique_code (int),
    "status": 404
    "error": "error_name"
  }
```
