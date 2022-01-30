# tiny-code-editor

Not only is it a simple editor of 300b, but you can also copy-paste the code snippets into a bookmark URL or directly into the address bar making it available offline as well.

<div style="font-size: 2rem">
<a href="http://lewdev.github.io/apps/tiny-code-editor">Demo</a>
</div>

## Copy-paste into Address Bar

I combined elements from [Mini Code Editor](https://xem.github.io/miniCodeEditor/) by [xem](https://twitter.com/MaximeEuziere) to create this live code editor with dark mode and spell check disabled.

*I'm not sure if these are technically "bookmarklets" since it was defined as code you can drop into bookmarkets that start with `javascript:`.

This is great for prototyping or using as a base-line for creating your own custom code editing tool to speed up development.

## Press "Ctrl + Enter" to run 
This is avoids the problem of the browser crashing as you're typing out a `while` loop.

### Vertical (324 chars)
```
data:text/html,<textarea id=d spellcheck=false></textarea><iframe id=f></iframe><script>onkeypress=e=>(e.ctrlKey&&e.keyCode==13)||e.keyCode==10?f.srcdoc=d.value:0</script><style>*{box-sizing:border-box;margin:0}textarea,iframe{width:50%;height:100%;vertical-align:top}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```
## Horizontal (305 chars)
```
data:text/html,<textarea id=d spellcheck=false></textarea><iframe id=f></iframe><script>onkeypress=e=>(e.ctrlKey&&e.keyCode==13)||e.keyCode==10?f.srcdoc=d.value:0</script><style>*{box-sizing:border-box;margin:0}textarea,iframe{width:100%;height:50%}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```

## Live Editor
This is great for HTML/CSS coding since you're less concerned about running into JavaScript issues. Just be careful not to write a `while` loop.

### Vertical (251 chars)
```
data:text/html,<textarea oninput=f.srcdoc=value spellcheck=false></textarea><iframe id=f></iframe><style>*{box-sizing:border-box;margin:0}textarea,iframe{width:50%;height:100%;vertical-align:top}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```
### Horizontal (232 chars)
```
data:text/html,<textarea oninput=f.srcdoc=value spellcheck=false></textarea><iframe id=f></iframe><style>*{box-sizing:border-box;margin:0}textarea,iframe{width:100%;height:50%}textarea{resize:none;filter:invert(1)hue-rotate(180deg)}
```

## Code with Comments
`data:text/html,` implies that the following text will be returned as an HTML document.
```
<!-- The browser's spellcheck doesn't like code  -->
<textarea id=d spellcheck=false></textarea>

<!-- This is where the code is run -->
<iframe id=f></iframe>

<!--
  Detect when Ctrl + Enter is pressed

  This is where the code in the textarea is put into the iframe:
    f.srcdoc = d.value
-->
<script>
onkeypress = e => (e.ctrlKey && e.keyCode==13) || e.keyCode==10 ? f.srcdoc = d.value : 0
</script>

<style>
/* Makes sure textarea and iframe are flush in the window */
* { box-sizing: border-box; margin: 0 }

textarea, iframe {
  /* Flip these values to change to horizontal layout. */
  width: 50%;
  height: 100%; 

  /*
    In Chrome, these two elements don't stay flush to the top of the window
    in vertical layout.
  */
  vertical-align: top;
}

textarea {
  /* Removes the resize capability since it grows/shrinks with the window. */
  resize:none;

  /* Dark mode for the textarea. Optional */
  filter: invert(1) hue-rotate(180deg)
}

/* No close style tag since it works without it and saves 8 characters.*/
```

## Run Source Code

Install global dependencies: [serve](https://www.npmjs.com/package/serve), [concurrently](https://www.npmjs.com/package/concurrently), [opener](https://www.npmjs.com/package/opener). These packages enable serving the code on a static server and opening it on your default web browser.
```
npm i
```

Run the code in `src` directory:
```
npm start
```

## Other minimalist bookmarklet editors

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
