# tiny-code-editor

Not only is it a simple editor of 300b, but you can also copy-paste the code snippets into a bookmark URL or directly into the address bar making it available offline as well.

<div style="font-size: 2rem">
<a href="http://lewdev.github.io/apps/tiny-code-editor">Demo</a>
</div>

## Copy-paste into Address Bar

I combined elements from [Mini Code Editor](https://xem.github.io/miniCodeEditor/) by [xem](https://twitter.com/MaximeEuziere) to create this live code editor with dark mode and spell check disabled.

*I'm not sure if these are technically "bookmarklets" since it was defined as code you can drop into bookmarkets that start with `javascript:`.

The main bug is when you have infinite loops in your code, it will require a refresh and that will clear your code. Also, this happens unintentionally since it reloads your code on every keypress.

This is great for prototyping and for creating your own custom tool to speed up development.

### Horizontal Split (289b) Press Ctrl + Enter to run code (when on the page)
```
data:text/html,<textarea id=d spellcheck=false></textarea><iframe id=f></iframe><script>onkeypress=e=>e.ctrlKey&&e.keyCode==13?f.srcdoc=d.value:0</script><style>*{box-sizing:border-box;margin:0}textarea,iframe{width:100%;height:50%}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```

### Vertical split (285b) Press Ctrl + Enter to run code (when on the page)
```
data:text/html,<textarea id=d spellcheck=false></textarea><iframe id=f></iframe><script>onkeypress=e=>e.ctrlKey&&e.keyCode==13?f.srcdoc=d.value:0</script><style>html,body{height:100%}*{box-sizing:border-box;margin:0}textarea,iframe{width:50%;height:100%}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```

## Run Code

Install global dependencies: [serve](https://www.npmjs.com/package/serve), [concurrently](https://www.npmjs.com/package/concurrently), [opener](https://www.npmjs.com/package/opener). These packages enable serving the code on a static server and opening it on your default web browser.
```
npm i
```

Run the code in `src` directory:
```
npm start
```

## Other minimal bookmarklet editors

### Minimal Text Editor (37b)
This one is good to memorize.
```
data:text/html,<html contenteditable>
```

### Text Editor (113b)
This is a fancy one with style from PC World.
```
data:text/html,<body contenteditable style="font:2rem/1.5 monospace;max-width:60rem;margin:0 auto;padding:4rem">
```

## Inspired by

* [Mini Code Editor](https://xem.github.io/miniCodeEditor/) by [xem](https://twitter.com/MaximeEuziere)
  * [Full Editor HTML/CSS/JS (1kb)](https://xem.github.io/miniCodeEditor/1.1/) by xem, which also allows code-sharing via URL.
* [Live Editor by tomhodgins](https://tomhodgins.github.io/liveeditor/index.html)
* [Turn any browser tab into a basic text editor](https://www.pcworld.com/article/2360940/turn-any-browser-tab-into-a-basic-text-editor.html) (PC World)
