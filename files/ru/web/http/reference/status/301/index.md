---
title: 301 Moved Permanently
slug: Web/HTTP/Reference/Status/301
---

Код перенаправления **`301 Moved Permanently`** протокола передачи гипертекста (HTTP) показывает, что запрошенный ресурс был окончательно перемещён в URL, указанный в заголовке {{HTTPHeader("Location")}}. Браузер в случае такого ответа перенаправляется на эту страницу, а поисковые системы обновляют свои ссылки на ресурс (говоря языком SEO, вес страницы переносится на новый URL-адрес).

Даже если спецификация требует, чтобы при выполнении перенаправления, метод и тело запроса не изменялись, не все пользовательские приложения обращают на это внимание, и вы все ещё можете столкнуться с программами имеющими этот баг. Именно поэтому код **301** рекомендуется только в качестве ответа на {{HTTPMethod("GET")}} или {{HTTPMethod("HEAD")}} запрос, а для {{HTTPMethod("POST")}} рекомендуется код {{HTTPStatus("308", "308 Permanent Redirect")}}, так как он явно запрещает изменение метода запроса.

## Статус

```
301 Moved Permanently
```

## Пример

### Запрос клиента

```
GET /index.php HTTP/1.1
Host: www.example.org
```

### Ответ сервера

```
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/index.asp
```

## Характеристики

| Спецификация                                          | Название                                                      |
| ----------------------------------------------------- | ------------------------------------------------------------- |
| {{RFC("7231", "301 Redirect Permanently" , "6.4.2")}} | Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content |

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{HTTPStatus("308", "308 Permanent Redirect")}}
- {{HTTPStatus("302", "302 Found")}}, временное перенаправление
