---
title: Получить Access Token по Session ID
description: Получить Access Token по Session ID
keywords: Получить Access Token по Session ID
sort: 0
---
 
# Получить Access Token по Session ID

POST **https://api.movika.com/accounts/identity/session**

Возвращает Access Token по Session ID.

## Тело запроса
| Параметр | Тип | Описание |
|---|---|---|---|
| sessionId | string | Идентификатор сессии |

<---- ## Параметры запроса

## Headers

| Заголовок | Тип  | Пример | Описание |
|---|---|---|---|
| Api-Version | string | 2.0 | Версия API | 
| Api-Key | string | {{apikey}} | Уникальный ключ API |


## Ответы сервера

## Ответ 200 - Successful

Ответ 200 Successful возвращается в случае успешного запроса на получение Access Token

Модель данных 

| Наименование | Тип | Описание |
|---|---|---|---|
| accessToken | string | Access Token |
| refreshToken | string | Refresh Token для получения следующего accessToken токена, после завершения срока действия последнего |
| uid | integer | ID пользователя |



Пример

```
{
  "accessToken": "pffkvi,voirmvdfkmskdfls",
  "refreshToken": "dksmflksdmvlsmvofomvfvo",
  "uid": 83315380
}
```


## Ответ 400 - Bad Request

Пример ответа

```
{
  "error": "Error name",
  "message": "Exception message",
  "path": "request/path/with/exception",
  "status": 400,
  "timestamp": "2015-01-22T03:41:02.000Z",
  "code": 1000,
  "service": "accounts"
}
```


## Ответ 401 - Unauthorized

Пример ответа

```
{
  "error": "Error name",
  "message": "Exception message",
  "path": "request/path/with/exception",
  "status": 401,
  "timestamp": "2015-01-22T03:41:02.000Z",
  "code": 1000,
  "service": "accounts"
}
```

## Ответ 403 - Forbidden

Пример ответа

```
{
  "error": "Error name",
  "message": "Exception message",
  "path": "request/path/with/exception",
  "status": 403,
  "timestamp": "2015-01-22T03:41:02.000Z",
  "code": 1000,
  "service": "accounts"
}
```