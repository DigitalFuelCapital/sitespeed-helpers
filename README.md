# sitespeed-helpers

## Async Link

```
<!-- inline styles needed for Optimal CRUX scores -->
<style>
  /* TODO: nav */
  /* TODO: #main */
  /* TODO: #hero */
  /* TODO: .above-the-fold-elements */
</style>

<!-- Simple: load main font via async link pattern -->
<link rel="stylesheet" href="/css/optional-and-additional.css" media="print" onload="this.media='all'">

<!-- More Advanced: https://www.digitalocean.com/community/tutorials/html-preload-prefetch -->
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

## img[loading="lazy"]

TLDR add `loading="lazy"` to every img and rip out all your img lazyloading js/plugins.

CanIUse: https://caniuse.com/loading-lazy-attr

Shopify `image_tag`: https://mikefallows.com/posts/responsive-images-in-shopify-themes/#the-new-image_tag-filter
