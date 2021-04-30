---
title: Получить проект
description: Получить проект
keywords: Получить проект
sort: 0
---
 
# Получить проект 

GET **https://api.movika.com/studio/{projectId}**

Возвращает проект интерактивного фильма по идентификатору **{projectId}**.


## Параметры запроса

### Параметр пути

| Параметр пути | Тип | Формат | Описание |
|---|---|---|
| projectId | integer | int64 | ID проекта |

## Headers

| Заголовок | Тип  | Пример | Описание |
|---|---|---|---|
| Authorization | string | Bearer {{accessToken}} | Токен пользователя с приставкой Bearer |
| Api-Version | string | 2.0 | Версия API | 
| Api-Key | string | {{apikey}} | Уникальный ключ API |


## Ответы сервера

## Ответ 200 - Successful

Ответ 200 Successful возвращается в случае успешного запроса на получение проекта интерактивного фильма

Модель данных Project 

| Наименование | Тип | Формат | Описание |
|---|---|---|---|
| id | integer | int64| ID проекта |
| title | string| | Заголовок проекта |
| cover | string | uri| Обложка проекта |
| duration | integer | int64| Длительность проекта в секундах |
| manifestUrl | string | uri| Ссылка на манифест проекта интерактивного видео |
| projectName | string| | Наименование проекта |
| status | integer | | Текущий статус проекта. Возможные значения: ["0": "IN_PROCCESS","1":"DONE","2":"ERROR","3":"TO_DEPLOY"] |
| projectType | integer | | | Типо проекта. Возможные значения: [ "1":"Pro", "2":"LiteEditor"] |
| keywords | string| | Ключевые слова, описывающие содержание проекта |
| linkOnly | boolean | | Проект доступен только по ссылке (Да/Нет) |
| createTime | string | yyyy-MM-dd'T'HH:mm:ss'Z' | Время создания проекта |
| author | Author | | Информация об авторе проекта |
| updateTime | string | yyyy-MM-dd'T'HH:mm:ss'Z'| Время последнего редактирования проекта |

Модель данных Author

| Наименование | Тип | Формат | Описание |
|---|---|---|---|
| id | integer | int64 | ID пользователя |
| avatarUri | string | uri | Ссылка на аватар автора |
| login | string || Логин автора |

Пример

```
{
  "id": 94851261,
  "title": "Title movika sdk sample",
  "duration": 60367587,
  "author": {
    "id": 40743843,
    "login": "Vadim",
    "firstName": "Vadim",
    "lastName": "Pupkov",
    "avatarUri": "https://movika.com/img/avatar.jpg"
  },
  "projectName": "movika-sdk-sample",
  "createTime": "2003-11-12T22:00:57.285Z",
  "updateTime": "2013-01-16T20:07:41.607Z",
  "cover": "https://movika.com/img/cover.jpg",
  "manifestUrl": "https://movika.com/ru/player/movika-sdk-sample",
  "status": 3,
  "projectType": 1,
  "keywords": "movika, sample",
  "linkOnly": false
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
  "code": 8000,
  "service": "studio"
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
  "code": 8000,
  "service": "studio"
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
  "code": 8000,
  "service": "studio"
}
```


## Ответ 404 - Not found

Пример ответа

```
{
  "error": "Error name",
  "message": "Exception message",
  "path": "request/path/with/exception",
  "status": 404,
  "timestamp": "2015-01-22T03:41:02.000Z",
  "code": 8000,
  "service": "studio"
}
```
