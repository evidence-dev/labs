<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    export let url;
</script>

<div class=container>
    <a class=sheet-link href={url} target="_blank" rel="noreferrer">Open in Google Sheets &rarr;</a>
    <iframe src={url} title="Google Sheet" width="1000"></iframe>
</div>

<style>
    .container {
        border: 1px solid var(--grey-300);
        border-radius: 4px;
        width: 100%;
        margin-bottom: 30px;
        padding: 2px;
    }
    iframe {
        width: 100%;
        height: 600px;
        border: none;
    }
    .sheet-link {
        float: left;
        padding-left: 10px;
        padding-top: 5px;
        font-size: 0.65em;
        font-family: sans-serif;
        color: var(--blue-600);
        text-decoration: none;
    }
    .sheet-link:hover {
        color: var(--blue-700);
    }
</style>