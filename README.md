# Svelte Typeform Embed

A Svelte wrapper component for
[Typeform Embed SDK](https://developer.typeform.com/embed/).

## Usage

```bash
npm install svelte-typeform-embed @rollup/plugin-replace
```

In your **.svelte** file:

```js
<script>
  import Typeform from "svelte-typeform-embed";
</script>

<Typeform url="https://peronalurl.typeform.com/to/1234" />
```

In **rollup.config.js** you need to add after **commonjs(),**:

```js
replace({ 'process.env.NODE_ENV': JSON.stringify( 'production' ) }),
```

### License

Code released under the [MIT license](LICENSE.md).
