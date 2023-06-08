<script>
    import FranceMap from "$lib/charts/maps/FranceMap.svelte";
    let world = [
        {
            country: "Canada",
            sales_usd: 100,
            link: "./canada",
        },
        {
            country: "United Kingdom",
            sales_usd: 50,
            link: "./canada",
        },
        {
            country: "France",
            sales_usd: 200,
            link: "./canada",
        },
        {
            country: "Argentina",
            sales_usd: 150,
            link: "./canada",
        },
        {
            country: "Mexico",
            sales_usd: 150,
            link: "./canada",
        },
        {
            country: "Chad",
            sales_usd: 65,
            link: "./canada",
        },
        {
            country: "Germany",
            sales_usd: 70,
            link: "./canada",
        },
        {
            country: "Egypt",
            sales_usd: 17,
            link: "./canada",
        },
        {
            country: "Greenland",
            sales_usd: 55,
            link: "./canada",
        },
        {
            country: "China",
            sales_usd: 155,
            link: "./canada",
        },
    ];

    let france = [
        {
            department: "Gironde",
            sales: 1000,
        },
        {
            department: "Cantal",
            sales: 2000,
        },
        {
            department: "Loir-et-Cher",
            sales: 888,
        },
        {
            department: "Seine-et-Marne",
            sales: 485,
        },
        {
            department: "Morbihan",
            sales: 294,
        },
        {
            department: "Vendée",
            sales: 998,
        },
    ];
</script>

<h1>Welcome to your library project</h1>
<p>
    Create your package using @sveltejs/package and preview/showcase your work
    with SvelteKit
</p>
<p>
    Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>

<FranceMap data={france} region="department" value="sales" />
