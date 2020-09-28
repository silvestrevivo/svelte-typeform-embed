<script>
    import * as typeformEmbed from '@typeform/embed';
    import { onMount } from 'svelte';

    export let url,
        style,
        popup = false,
        //general options
        hideHeaders = false,
        hideFooter = false,
        hideScrollbars = true,
        onSubmit = () => {},
        onReady = () => {},
        // widget mode
        opacity = 100,
        buttonText = 'Start',
        //popup
        mode = 'popup',
        autoOpen = false,
        autoClose = 0;

    export let typeformPopup;

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
        const options = {
            hideHeaders,
            hideFooter,
            hideScrollbars,
            onSubmit,
            onReady,
        };
        if (!popup) {
            typeformEmbed.makeWidget(myElement, url, {
                ...options,
                opacity,
                buttonText,
            });
        } else {
            typeformPopup = typeformEmbed.makePopup(url, {
                ...options,
                mode,
                autoOpen,
                autoClose,
            });
            return typeformPopup;
        }
    });
</script>

<div id="svelte-typeform-embed" style={styleApplyed} bind:this={myElement} />
