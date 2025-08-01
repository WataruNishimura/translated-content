---
title: Intl.NumberFormat
slug: Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat
l10n:
  sourceCommit: 544b843570cb08d1474cfc5ec03ffb9f4edc0166
---

**`Intl.NumberFormat`** オブジェクトは、言語に依存した数値書式を可能にするオブジェクトのコンストラクターです。

{{InteractiveExample("JavaScript デモ: Intl.NumberFormat")}}

```js interactive-example
const number = 123456.789;

console.log(
  new Intl.NumberFormat("de-DE", { style: "currency", currency: "EUR" }).format(
    number,
  ),
);
// 予想される結果: "123.456,79 €"

// 日本円は副単位を使用しない
console.log(
  new Intl.NumberFormat("ja-JP", { style: "currency", currency: "JPY" }).format(
    number,
  ),
);
// 予想される結果: "￥123,457"

// 有効桁数を 3 桁に制限
console.log(
  new Intl.NumberFormat("en-IN", { maximumSignificantDigits: 3 }).format(
    number,
  ),
);
// 予想される結果: "1,23,000"
```

## コンストラクター

- {{jsxref("Intl/NumberFormat/NumberFormat", "Intl.NumberFormat()")}}
  - : 新しい `NumberFormat` オブジェクトを生成します。

## 静的メソッド

- {{jsxref("Intl/NumberFormat/supportedLocalesOf", "Intl.NumberFormat.supportedLocalesOf()")}}
  - : 提供されたロケールのうち、実行時の既定のロケールに代替せずに対応しているものを配列に収めて返します。

## インスタンスプロパティ

これらのプロパティは `Intl.NumberFormat.prototype` で定義されており、すべての `Intl.NumberFormat` インスタンスで共有されます。

- {{jsxref("Object/constructor", "Intl.NumberFormat.prototype.constructor")}}
  - : インスタンスオブジェクトを作成したコンストラクター関数。 `Intl.NumberFormat` インスタンスの場合、初期値は {{jsxref("Intl/NumberFormat/NumberFormat", "Intl.NumberFormat")}} コンストラクターです。
- `Intl.NumberFormat.prototype[Symbol.toStringTag]`
  - : [`[Symbol.toStringTag]`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Symbol/toStringTag) プロパティの初期値は、文字列 `"Intl.NumberFormat"` です。このプロパティは {{jsxref("Object.prototype.toString()")}} で使用されます。

## インスタンスメソッド

- {{jsxref("Intl/NumberFormat/format", "Intl.NumberFormat.prototype.format()")}}
  - : ゲッター関数で、ロケールに応じて、この `Intl.NumberFormat` オブジェクトのオプションを持つ数値を書式化する関数を返します。
- {{jsxref("Intl/NumberFormat/formatRange", "Intl.NumberFormat.prototype.formatRange()")}}
  - : ゲッター関数で、メソッドが呼び出された `Intl.NumberFormat` オブジェクトのロケールおよび書式設定オプションに従って、数値の範囲を書式化します。
- {{jsxref("Intl/NumberFormat/formatRangeToParts", "Intl.NumberFormat.prototype.formatRangeToParts()")}}
  - : オブジェクトの {{jsxref("Array")}} を返し、これは専用のロケールを意識した書式で使用することができる部品内の数値文字列を表します。
- {{jsxref("Intl/NumberFormat/formatToParts", "Intl.NumberFormat.prototype.formatToParts()")}}
  - : {{jsxref("Array")}} で、カスタムロケールに対応した書式化に使用できる、数値文字列を表すオブジェクトの配列を返します。
- {{jsxref("Intl/NumberFormat/resolvedOptions", "Intl.NumberFormat.prototype.resolvedOptions()")}}
  - : ロケールを反映しているプロパティとオブジェクトの初期化中に計算された照合オプションをもった新しいオブジェクトを返します。

## 例

### 基本的な使用

ロケールを指定しない基本的な使い方では、既定のロケールとオプションで書式化された文字列が返されます。

```js
const number = 3500;

console.log(new Intl.NumberFormat().format(number));
// '3,500' 英語 (US) ロケールの場合
```

### locales の使用

この例では、地域による数値書式の違いをいくつか紹介します。アプリケーションのユーザーインターフェイスで使われた言語書式を得るには、言語 (およびフォールバック言語) を `locales` 引数により指定してください。

```js
const number = 123456.789;

// ドイツではカンマを小数、ピリオドを千単位の区切りに用います
console.log(new Intl.NumberFormat("de-DE").format(number));
// 123.456,789

// ほとんどのアラビア語圏ではアラビア数字を用います
console.log(new Intl.NumberFormat("ar-EG").format(number));
// ١٢٣٤٥٦٫٧٨٩

// インドでは thousands/lakh/crore 区切りが用いられます
console.log(new Intl.NumberFormat("en-IN").format(number));
// 1,23,456.789

// nu 拡張キーにより漢数字などの番号方式が使えます
console.log(new Intl.NumberFormat("zh-Hans-CN-u-nu-hanidec").format(number));
// 一二三,四五六.七八九

// バリ語のように対応していない可能性がある言語を用いる場合は
// 代替言語を含めます。次の例ではインドネシア語です
console.log(new Intl.NumberFormat(["ban", "id"]).format(number));
// 123.456,789
```

### options の使用

[`options`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#options) 引数を使うと、結果をカスタマイズできます。

```js
const number = 123456.789;

// 通貨の書式を用います
console.log(
  new Intl.NumberFormat("de-DE", { style: "currency", currency: "EUR" }).format(
    number,
  ),
);
// 123.456,79 €

// 日本円には副単位がありません
console.log(
  new Intl.NumberFormat("ja-JP", { style: "currency", currency: "JPY" }).format(
    number,
  ),
);
// ￥123,457

// 有効数字を 3 桁に狭めます
console.log(
  new Intl.NumberFormat("en-IN", { maximumSignificantDigits: 3 }).format(
    number,
  ),
);
// 1,23,000

// 単位付きの整形
console.log(
  new Intl.NumberFormat("pt-PT", {
    style: "unit",
    unit: "kilometer-per-hour",
  }).format(50),
);
// 50 km/h

console.log(
  (16).toLocaleString("en-GB", {
    style: "unit",
    unit: "liter",
    unitDisplay: "long",
  }),
);
// 16 litres
```

オプションの完全なリストについては、 [`Intl.NumberFormat()` コンストラクター](/ja/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#options)ページを参照してください。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [`Intl.NumberFormat` のポリフィル (FormatJS)](https://formatjs.github.io/docs/polyfills/intl-numberformat/)
- {{jsxref("Intl")}}
- {{jsxref("Number.prototype.toLocaleString()")}}
