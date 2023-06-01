<script>
    import { onMount } from "svelte";

    const endpoint = `https://www.google.fr/alerts/feeds/15619974748131115017/10276471069386552675`;

    let posts = [];

    onMount(async function () {
        const response = await fetch(endpoint);
        let data = await response.text();
        console.log(data)
        return (posts = [data.articles]);
    });


</script>

<main>
    <h1>News RSS Feed - Authentification</h1>
    <p>
        News from [LINK OF WEBSITE] rss feed.
    </p>

    <div class="articles">
            <div class="articles">
            </div>
    </div>
</main>

<style>
</style>
