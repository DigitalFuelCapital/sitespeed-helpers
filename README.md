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

<!-- Simple: load main css via async link pattern (media=print doesn't block) -->
<link rel="stylesheet" href="/css/optional-and-additional.css" media="print" onload="this.media='all'">

<!-- 
  Other CSS Pattern explanation & notes: 
  https://www.digitalocean.com/community/tutorials/html-preload-prefetch 
-->
```

## Async Font

Ideal State. Load font-face + woff2 ref as inline style with `font-display: swap;`:

```html
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
<!-- load main font via async link pattern (media=print doesn't block) -->
<link rel="stylesheet" href="/css/fontello.css" media="print" onload="this.media='all'">

<!-- also preload woff2 -->
<link rel="preload" href="/fonts/fontello.woff2?98303082" as="font" type="font/woff2" crossorigin>

<!-- TODO: Google "Add font-display: swap; to ${fontHost}" if something like google font -->
<!-- e.g., https://css-tricks.com/the-fastest-google-fonts/ -->
```

## img[loading="lazy"]

TLDR add `loading="lazy"` to every img and rip out all your img lazyloading js/plugins.

CanIUse: https://caniuse.com/loading-lazy-attr

Shopify Example ([docs](https://mikefallows.com/posts/responsive-images-in-shopify-themes/#the-new-image_tag-filter))

```liquid
<!-- Shopify Responsive `image_tag` -->
{{ settings.banner | image_url: width: 2000 | image_tag: loading: "lazy" }}
```

HTML Examples:

```html
<!-- This is above the fold so no lazy -->
<img src="/home-hero.jpg" alt="Shop Brand" />

<!-- this is below so yes lazy -->
<img src="footer/social-icon-facebook.jpg" alt="facebook" loading="lazy"/>
<img src="footer/social-icon-twitter.jpg" alt="twitter" loading="lazy"/>
<img src="footer/social-icon-pinterest.jpg" alt="pinterest" loading="lazy"/>
```

More examples from: https://addyosmani.com/blog/lazy-loading/

```html
<!-- Lazy-load an offscreen image when the user scrolls near it -->
<img src="unicorn.jpg" loading="lazy" alt=".."/>

<!-- Load an image right away instead of lazy-loading -->
<img src="unicorn.jpg" loading="eager" alt=".."/>

<!-- Browser decides whether or not to lazy-load the image -->
<img src="unicorn.jpg" loading="auto" alt=".."/>

<!-- Lazy-load images in <picture>. <img> is the one driving image 
loading so <picture> and srcset fall off of that -->
<picture>
  <source media="(min-width: 40em)" srcset="big.jpg 1x, big-hd.jpg 2x">
  <source srcset="small.jpg 1x, small-hd.jpg 2x">
  <img src="fallback.jpg" loading="lazy">
</picture>

<!-- Lazy-load an image that has srcset specified -->
<img src="small.jpg"
     srcset="large.jpg 1024w, medium.jpg 640w, small.jpg 320w"
     sizes="(min-width: 36em) 33.3vw, 100vw"
     alt="A rad wolf" loading="lazy">

<!-- Lazy-load an offscreen iframe when the user scrolls near it -->
<iframe src="video-player.html" loading="lazy"></iframe>
```

## Error Monitoring

https://cdn.catchjs.com/catch.js
