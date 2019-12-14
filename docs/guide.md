## Sidebar

In order to have sidebar, then you can create your own `_sidebar.md` (see [this documentation's sidebar](https://github.com/docsifyjs/docsify/blob/master/docs/_sidebar.md) for an example):

First, you need to set `loadSidebar` to **true**. Details are available in the [configuration paragraph](configuration.md#loadsidebar).
Test HTML Snippet

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```