---
layout:     post
title:      Formatting monetary values
date:       2022-09-08
categories: Javascript
---
<style>
    .codeblock-label {
        display: inline-block;
        border-top-left-radius: 0.5rem;
        border-top-right-radius: 0.5rem;
        font-family: Menlo,Monaco,Consolas,Liberation Mono,Courier New,monospace;
        font-size: 0.75rem;
        padding: 0.25rem 0.75rem;
        border-style: solid;
        border-color: rgba(0, 0, 0, .5);
        border-width: 1px 1px 0 1px;
        margin-bottom: 0;
    }
</style>
# Money Money Money

```javascript
function formatMoney(number) {
  return number.toLocaleString('en-GB', { style: 'currency', currency: 'GBP' });
}

const amount = 123456;
console.log(formatMoney(amount));
```

<p class="codeblock-label">Console Output</p>

```
£123,456.00
```
