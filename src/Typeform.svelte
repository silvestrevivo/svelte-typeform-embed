<script>
    import * as typeformEmbed from '@typeform/embed';
    import { onMount } from 'svelte';

    export let url, style;

    let myElement;
    let styleByDefault = {
        position: 'absolute',
        top: 0,
        left: 0,
        width: '100%',
        height: '100%',
        overflow: 'hidden',
    };

    function styleString(style) {
        return Object.entries(style)
            .map(([k, v]) => `${k}:${v}`)
            .join(';');
    }

    $: styleApplyed = styleString({ ...styleByDefault, ...style });

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

<div id="svelte-typeform-embed" style={styleApplyed} bind:this={myElement} />
