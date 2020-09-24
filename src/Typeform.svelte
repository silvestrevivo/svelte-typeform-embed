<script>
    import * as typeformEmbed from '@typeform/embed';
    import { onMount } from 'svelte';

    export let url;

    let myElement;

    onMount(() => {
        typeformEmbed.makeWidget(myElement, url, {
            opacity: 55,
            buttonText: 'Answer this!',
            hideScrollbars: true,
            onSubmit: function () {
                console.log('Typeform successfully submitted');
            },
            onReady: function () {
                console.log('Typeform is ready');
            },
        });
    });
</script>

<div
    id="svelte-typeform-embed"
    style="width: 100%; height: 700px"
    bind:this={myElement} />
