---
id: html
title: HTML
---

How to use in HTML:

```
<!-- place once in your HTML at the top -->
<script src="https://moneybutton.com/moneybutton.js" />
```

```
<!-- place your button(s) anywhere you want in your HTML -->
<div class="money-button"
  data-to=[to]
  data-type=[type]
  data-amount=[amount]
  data-currency=[currency]
  data-op-return=[op-return]
  data-outputs=[outputs]
  data-owner-id=[owner-id]
  data-button-id=[button-id]
  data-button-data=[button-data]
  data-callback=[callback]
  data-size=[size]
  data-color=[color]
  data-hide-amount=[hide-amount]
  data-dropdown=[dropdown]
/>
```

The MoneyButton div can take a number of params:

| prop               | type                                      | default value |
| ------------------ | ----------------------------------------- | ------------- |
| `data-type`        | `string` (`'pay', 'tip'`)                 | `'pay'`       |
| `data-to`          | `string` (either a BCH address or userId) | Yours Inc.    |
| `data-amount`      | `string`                                  | `null`        |
| `data-currency`    | `string` (`USD`, `BCH`, etc.)             | `'USD'`       |
| `data-op-return`   | `string`                                  | `null`        |
| `data-outputs`     | `array`                                   | `[]`          |
| `data-owner-id`    | `string`                                  | `null`        |
| `data-button-id`   | `string`                                  | `null`        |
| `data-button-data` | `string`                                  | `null`        |
| `data-size`        | `string`                                  | `'med'`       |
| `data-color`       | `string`                                  | `'light'`     |
| `data-callback`    | `string`                                  | `null`        |

`outputs` is a JSON stringified list of `output` objects. Each `output` object has these parameters:

| name       | type                          | required? |
| ---------- | ----------------------------- | --------- |
| `address`  | `string` (`'pay', 'tip'`)     | optional  |
| `userId`   | `string`                      | optional  |
| `script`   | `string`                      | optional  |
| `amount`   | `string`                      | required  |
| `currency` | `string` (`USD`, `BCH`, etc.) | required  |

Also, the `callback` string is actually the name of a function in the global namespace. That function must look like this:

```
function myCallback (err, payment) {
    // ...
}
```

Where the `payment` is an object that looks like this:

| name         | type     |
| ------------ | -------- |
| `id`         | `string` |
| `buttonId`   | `string` |
| `buttonData` | `string` |
| `status`     | `string` |
| `txid`       | `string` |
| `ntxid`      | `string` |
| `amount`     | `string` |
| `currency`   | `string` |
| `satoshis`   | `string` |
| `outputs`    | `array`  |

Where in this case the outputs are slightly more sophisticated:

| name       | type                                       |
| ---------- | ------------------------------------------ |
| `type`     | `string` (`'address', 'userId', 'script'`) |
| `address`  | `string`                                   |
| `userId`   | `string`                                   |
| `script`   | `string`                                   |
| `amount`   | `string`                                   |
| `currency` | `string`                                   |
| `satoshis` | `number`                                   |