---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: sishui' blog
  text: 
  tagline: A blog that shares technology.
  image:
    src: /public/headshot.jpg
    alt: headshot
  actions:
    - theme: alt
      text: View on GitHub
      link: https://github.com/inspiringforever/VitePress-Blog
    - theme: brand
      text: Get Started
      link: /tutorials/index.md
features:
  - icon: 🛠️
    title: Simple and minimal, always
    details: Lorem ipsum...
  - icon:
      src: /public/favicon.png
    title: Another cool feature
    details: Lorem ipsum...
  - icon: 🌰
    title: Example
    details: Lorem ipsum...
    link: /examples/index.md
---



<style>
:root {
  --vp-home-hero-name-color: transparent;
  --vp-home-hero-name-background: -webkit-linear-gradient(120deg, #bd34fe 30%, #41d1ff);

  --vp-home-hero-image-background-image: linear-gradient(-45deg, #bd34fe 50%, #47caff 50%);
  --vp-home-hero-image-filter: blur(44px);
}

@media (min-width: 640px) {
  :root {
    --vp-home-hero-image-filter: blur(56px);
  }
}

@media (min-width: 960px) {
  :root {
    --vp-home-hero-image-filter: blur(68px);
  }
}
</style>


