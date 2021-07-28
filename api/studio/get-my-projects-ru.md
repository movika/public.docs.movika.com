---
title: Получить все проекты текущего пользователя
description: Получить все проекты текущего пользователя
keywords: Получить все проекты текущего пользователя
sort: 1
---
 
# Получить все проекты текущего пользователя

GET **https://api.movika.com/studio-pro/my**

Возвращает список проектов интерактивных фильмов текущего пользователя с пагинацией.


## Параметры запроса

## Headers

| Заголовок | Тип  | Пример | Описание |
|---|---|---|---|
| Authorization | string | Bearer {{accessToken}} | Токен пользователя с приставкой Bearer |
| Api-Version | string | 2.0 | Версия API | 
| Api-Key | string | {{apikey}} | Уникальный ключ API |


## Ответы сервера

## Ответ 200 - Successful

Ответ 200 Successful возвращается в случае успешного запроса на получение списка проектов интерактивных фильмов

Модель данных Project 

| Наименование | Тип | Формат | Описание |
|---|---|---|---|
| id | integer | int64| ID проекта |
| title | string| | Заголовок проекта |
| cover | string | uri| Обложка проекта |
| manifestChanges | string | | Изменения с последней сборки проекта |
| lastBuiltManifestUrl | string | uri | Ссылка на последний собранный манифест проекта интерактивного видео |
| currentManifestUrl | string | uri | Ссылка на текущий манифест проекта интерактивного видео |
| author | Author | | Информация об авторе проекта |
| projectName | string| | Наименование проекта |
| buildStatus | integer | | Текущий статус сборки проекта. Возможные значения: [0:NOT_BUILT, 1:BUILDING, 2:BUILT, 3:ERROR] |
| lastBuildStatus | integer | | Последний статус сборки проекта. Возможные значения: [0:NOT_BUILT, 1:BUILDING, 2:BUILT, 3:ERROR] |
| keywords | string| | Ключевые слова, описывающие содержание проекта |
| deployStatus | integer| | Статус публикации проекта. Возможные значения: [0:NOT_DEPLOYED, 1:DEPLOYING, 2:DEPLOYED, 3:ERROR] |
| lastDeployType | integer| | Последний используемый тип публикации проекта. Возможные значения: [0:UNKNOWN, 1:TV, 2:URL] |
| deployedTo | array[integer]| | Используемые типы публикации проекта. Возможные значения: [0:UNKNOWN, 1:TV, 2:URL] |
| modified | boolean | | Проект модифицировался с момента последней сборки (Да/Нет) |
| created | string | yyyy-MM-dd'T'HH:mm:ss'Z' | Время создания проекта |
| updatedBy | string | email | Информация о последнем вносившем изменения в проект пользователе |
| updated | string | yyyy-MM-dd'T'HH:mm:ss'Z'| Время последнего редактирования проекта |

Модель данных Author

| Наименование | Тип | Формат | Описание |
|---|---|---|---|
| id | integer | int64 | ID пользователя |
| avatarUri | string | uri | Ссылка на аватар автора |
| login | string || Логин автора |
| firstName | string || Имя автора (если указано) |
| lastName | string || Фамилия автора (если указано) |

Пример

```
{
  "data": [
    {
      "id": 90280470,
      "title": "Excepteur in dolor",
      "cover": "http://BGHzcKuudfOLjUePkBUtyyVIoVR.cizaogwQLrTo.-hcCeEpqa.MKGzG+2fNhnz6OqWgr0OLgFae8tZp",
      "manifestChanges": "pariatur velit irure",
      "lastBuiltManifestUrl": "http://RgBIyxAPoxUsDRNNMwEUqhHvnsKaxerD.kmgyh1ypoFWmFoq86XFZ7RAceC2wYKBDYv+fjVZVEXYL61spd6NTPSrPh4",
      "currentManifestUrl": "https://bKGXVmHs.djN",
      "author": {
        "id": 29396578,
        "avatarUri": "https://xQDCFiinfapoXThcqKnNCi.dcgT6uL+EfF-xinSaSRM+qo9IAMlwKyNm8T8lVHlzy+M+8.",
        "login": "Ut dolore",
        "firstName": "in exercitation",
        "lastName": "aliquip ea proident incididunt magna"
      },
      "projectName": "suq1ZiyKk3UEMXYla0AP",
      "buildStatus": 0,
      "lastBuildStatus": 0,
      "keywords": "consectetur commodo laborum eu",
      "deployStatus": 3,
      "lastDeployType": 0,
      "deployedTo": [
        1,
        2
      ],
      "modified": false,
      "created": "1954-04-22T23:00:04.371Z",
      "updatedBy": "hJmjMh@pFk.opye",
      "updated": "1983-03-12T04:50:40.438Z"
    }
  ],
  "paging": {
    "after": "2",
    "before": "0"
  }
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
  "code": 16000,
  "service": "studio-pro"
}
```
