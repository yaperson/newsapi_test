<script>
    import { onMount } from "svelte";

    let API_KEY = "fe23749356bf415eac5eb72223169056";
    const endpoint = `https://newsapi.org/v2/everything?q=Authentification&apiKey=${API_KEY}`;

    let posts = [];

    onMount(async function () {
        const response = await fetch(endpoint);
        let data = await response.json();
        return (posts = [data.articles]);
    });

</script>

<main>
    <h1>News API - Authentification</h1>
    <p>
        News from newsapi, for france and with filter "Authentification".
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
                    <span> |date : {article.publishedAt}</span>
                {/if}    
                {/each}
            </div>
        {/each}
    </div>
</main>

<style>
</style>
