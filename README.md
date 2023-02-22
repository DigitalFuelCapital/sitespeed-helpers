# sitespeed-helpers

## Async Link

```html
<!-- inline styles needed for Optimal CRUX scores -->
<style>
  /* TODO: nav */
  /* TODO: #main */
  /* TODO: #hero */
  /* TODO: .above-the-fold-elements */
</style>

<!-- Simple: load main font via async link pattern (media=print doesn't block) -->
<link rel="stylesheet" href="/css/optional-and-additional.css" media="print" onload="this.media='all'">

<!-- 
  Other CSS Pattern explanation & notes: 
  https://www.digitalocean.com/community/tutorials/html-preload-prefetch 
-->
```

## Async Font

Ideal State. Load font-face + woff2 ref as inline style:

```html
<!-- PREFERRED:  -->
<style>
@font-face {
  font-display: swap;
  font-family: 'fontello';
  src: url('/fonts/fontello.woff2?98303082') format('woff2');
  font-weight: normal;
  font-style: normal;
}
</style>
<!-- also preload woff2 -->
<link rel="preload" href="/fonts/fontello.woff2?98303082" as="font" type="font/woff2" crossorigin>
```

Less Ideal but also a refactor option based on hosting / tech stack: 

```html
<!-- load font via async link pattern -->
<link rel="stylesheet" href="/css/fontello.css" media="print" onload="this.media='all'">
<!-- also preload woff2 -->
<link rel="preload" href="/fonts/fontello.woff2?98303082" as="font" type="font/woff2" crossorigin>
```

## img[loading="lazy"]

TLDR add `loading="lazy"` to every img and rip out all your img lazyloading js/plugins.

CanIUse: https://caniuse.com/loading-lazy-attr

Shopify `image_tag`: https://mikefallows.com/posts/responsive-images-in-shopify-themes/#the-new-image_tag-filter
