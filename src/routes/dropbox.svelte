<svelte:head>
    <title>Dropbox Embedder</title>
    <script async defer src="https://www.dropbox.com/static/api/2/dropins.js" id="dropboxjs" data-app-key="{__myapp.env.DROPBOX_APP_KEY}" on:load={onLoadDropbox}></script>
</svelte:head>

<script>
    import { onMount } from 'svelte';

    let embedder;
    let shareLink;

    onMount(() => {
        const url = new URL(document.URL);
        const searchParams = url.searchParams;
        shareLink = searchParams.get('share_link');

        if (shareLink && window.Dropbox) {
            embedWidget();
        }

        return unmountWidget;
    });

    function onLoadDropbox () {
        if (shareLink && window.Dropbox) {
            embedWidget();
        }
    }

    function embedWidget() {
        // Time for Dropbox to do its magic.
        let options = {
            // Shared link to Dropbox file
            link: shareLink,
            file: {
                zoom: "best" // or "fit"
            },
            folder: {
                view: "grid", // or "grid"
                headerSize: "normal" // or "small"
            }
        };
        if (typeof Dropbox !== undefined) {
            embedder = Dropbox.embed(options, document.getElementById('dropbox-widget'));
        }
    }

    function unmountWidget() {
        Dropbox.unmount(embedder);
    };
</script>

<div id="dropbox-widget"></div>

<a href="/">Home</a>

<style>
	#dropbox-widget {
		width: 100%;
		height: 100vh;
	}
</style>