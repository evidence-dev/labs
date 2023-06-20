<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import Footnote from "../../../../../src/lib/ui/Footnote.svelte";
</script>

# Footnote
A simple footnote component
<br/>

<Footnote id=1>
The data for this report was sourced from the World Bank World Development Indicators dataset.
</Footnote>

```html
<Footnote id=1>
The data for this report was sourced from the World Bank World Development Indicators dataset.
</Footnote>
```

<Footnote id=3>
Another footnote
</Footnote>

```html
<Footnote id=3>
Another footnote
</Footnote>
```

<Footnote>
Footnote without an id
</Footnote>

```html
<Footnote>
Footnote without an id
</Footnote>
```