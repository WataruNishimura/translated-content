---
title: Access-Control-Request-Headers
slug: Web/HTTP/Reference/Headers/Access-Control-Request-Headers
original_slug: Web/HTTP/Headers/Access-Control-Request-Headers
---

**`Access-Control-Request-Headers`** リクエストヘッダーは{{glossary("preflight request", "プリフライトリクエスト")}}を発行する際にブラウザーが使用し、実際のリクエストが行う際にどの [HTTP ヘッダー](/ja/docs/Web/HTTP/Reference/Headers)を使用するかをサーバーに知らせます。

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">ヘッダー種別</th>
      <td>
        {{Glossary("Request header", "リクエストヘッダー")}}
      </td>
    </tr>
    <tr>
      <th scope="row">
        {{Glossary("Forbidden request header", "禁止リクエストヘッダー")}}
      </th>
      <td>はい</td>
    </tr>
  </tbody>
</table>

## 構文

```
Access-Control-Request-Headers: <header-name>, <header-name>, ...
```

## ディレクティブ

- \<header-name>
  - : リクエストに含まれる [HTTP ヘッダー](/ja/docs/Web/HTTP/Reference/Headers)のカンマ区切りのリスト。

## 例

```
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{HTTPHeader("Access-Control-Request-Method")}}
