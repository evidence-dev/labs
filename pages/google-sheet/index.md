<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import GoogleSheet from "../../../../../src/lib/ui/GoogleSheet.svelte";
</script>

# Google Sheet Embed

Using the default Google Sheets URL:
```html
<GoogleSheet url='https://docs.google.com/spreadsheets/d/15xPK6IJkaj3XGyGDfesDqlGfBfq7dBMbMp3fH7epRGA/edit?usp=sharing'/>
```

<GoogleSheet url='https://docs.google.com/spreadsheets/d/15xPK6IJkaj3XGyGDfesDqlGfBfq7dBMbMp3fH7epRGA/edit?usp=sharing'/>

Using the "Publish" URL provided when you publish a Google Sheet publicly:
```html
<GoogleSheet url='https://docs.google.com/spreadsheets/d/e/2PACX-1vS4CmyhVsSYtVtK8MwyZ6WqkcEf1oxCx15zq-dZDitvCZt7alqYBy-ydnxJiApR-gD7oLsDY4s4V_sa/pubhtml?widget=true&amp;headers=false'/>
```

<GoogleSheet url='https://docs.google.com/spreadsheets/d/e/2PACX-1vS4CmyhVsSYtVtK8MwyZ6WqkcEf1oxCx15zq-dZDitvCZt7alqYBy-ydnxJiApR-gD7oLsDY4s4V_sa/pubhtml?widget=true&amp;headers=false'/>

