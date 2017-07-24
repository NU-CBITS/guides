# Patterns - web

## Embedding Vimeo iframe responsively

The default embed code provided by Vimeo embeds a fixed size video. To make it
responsive, one approach is to wrap it in a div:

````html
<style>
.video-container {
  position: relative;
  padding-bottom: 56.25%;
  padding-top: 35px;
  height: 0;
  overflow: hidden;
}

.video-container iframe {
  position: absolute;
  top:0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>

<div class="video-container">
  <iframe
    src="https://player.vimeo.com/video/159135336"
    frameborder="0"
    webkitallowfullscreen
    mozallowfullscreen
    allowfullscreen></iframe>
</div>
```
