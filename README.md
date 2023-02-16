# sitespeed-helpers

## Async Link

```
<style>
  /* TODO: nav */
  /* TODO: #main */
  /* TODO: #hero */
  /* TODO: .above-the-fold-elements */
</style>

<!-- load main font via async link pattern -->
<link rel="stylesheet" href="/css/optional-and-additional.css" media="print" onload="this.media='all'">
```

## Async Font

```
<!-- load main font via async link pattern -->
<link rel="stylesheet" href="/csss/fontello.css" media="print" onload="this.media='all'">

<!-- preload woff2 b/c most browsers -->
<link rel="preload" href="/fonts/fontello.woff2?98303082" as="font" type="font/woff2" crossorigin>

<!-- cp + load face declaration inline as well (optional) -->
<style>
@font-face {
  font-display: swap;
  font-family: 'fontello';
  src: url('/fonts/fontello.woff2?98303082') format('woff2');
  font-weight: normal;
  font-style: normal;
}
</style>
```
