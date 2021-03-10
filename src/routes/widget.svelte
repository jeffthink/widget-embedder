<svelte:head>
    <title>Widget Embedder</title>
</svelte:head>

<script>
    import { onMount } from 'svelte';

    let embedLink;

    onMount(() => {
        const url = new URL(document.URL);
        const searchParams = url.searchParams;
        embedLink = searchParams.get('link');
    });
</script>

<div id="widget">
    <iframe title="Widget Embedder" allowfullscreen frameborder="0" src="{embedLink}"></iframe>
</div>

<style>
	#widget, #widget iframe {
		width: 100%;
		height: 100vh;
	}
</style>