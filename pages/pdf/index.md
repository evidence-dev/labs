<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import PDF from "../../../../../src/lib/ui/PDF.svelte";
</script>

# PDF Embed

You may not be able to see the file using VS Code's built-in Simple Browser. If that is the case, use an external browser.

```html
<PDF path='../hn-insight.pdf'/>
```

<PDF path='../hn-insight.pdf'/>

## Without Toolbar

```html
<PDF path='../hn-insight.pdf' toolbar=false/>
```

<PDF path='../hn-insight.pdf' toolbar=false/>

## Custom Height

```html
<PDF path='../hn-insight.pdf' height=800/>
```

<PDF path='../hn-insight.pdf' height=800/>

## Open to Specific Page

```html
<PDF path='../hn-insight.pdf' page=3/>
```

<PDF path='../hn-insight.pdf' page=3/>

