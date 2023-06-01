<script>
    import { onMount } from "svelte";

    let API_KEY = "fe23749356bf415eac5eb72223169056";
    const endpoint = `https://newsapi.org/v2/everything?q=Authentification&from=2023-05-01&sortBy=popularity&apiKey=${API_KEY}`;

    let posts = [];

    onMount(async function () {
        const response = await fetch(endpoint);
        let data = await response.json();
        return (posts = [data.articles]);
    });

    export let name;
</script>

<main>
    <h1>News API - Authentification</h1>
    <h1>Hello {name}!</h1>
    <p>
        Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
        how to build Svelte apps.
    </p>

    <div class="articles">
        {#each posts as articles}
            <div class="articles">
                {#each articles as article}
                {#if  
                    article.content.indexOf("authentification") !== -1 ||
                    article.description.indexOf("authentification") !== -1 ||
                    article.title.indexOf("authentification") !== -1}
                    <h3>{ article.title }</h3>
                    <p>{ article.description }</p>
                    <img src="{article.urlToImage}" alt="">
                    <span>source : {article.source.name}</span>
                {/if}    
                {/each}
            </div>
        {/each}
    </div>
</main>

<style>
</style>
