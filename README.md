# Svelte Typeform Embed

A Svelte wrapper component for
[Typeform Embed SDK](https://developer.typeform.com/embed/).

## Installation

```bash
npm install svelte-typeform-embed @rollup/plugin-replace
```

In your **.svelte** file:

```html
<script>
    import Typeform from 'svelte-typeform-embed';
</script>

<Typeform url="https://mypersonalurl.typeform.com/to/1234" />
```

In **rollup.config.js** you need to add after **commonjs(),**:

```js
replace({ 'process.env.NODE_ENV': JSON.stringify( 'production' ) }),
```

## Demo

See a [live demo](https://svelte-typeform-embed.netlify.app/).

## Props

All the props are based in the official documentation from from
[Typeform Embed SDK](https://developer.typeform.com/embed/)

| Prop          | Description                                                                                                                                                                                                                                                                            | Default   |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| `url`         | Url you get from Typeform to display the form                                                                                                                                                                                                                                          | `""`      |
| `style`       | Additional styles for the component                                                                                                                                                                                                                                                    | `{}`      |
| `popup`       | `true` if you want to display the form in **popup** mode.<br />By default it is displayed in **widget** mode                                                                                                                                                                           | `false`   |
| `hideHeaders` | `true` if you want to hide the **header** that displays for question groups and long questions that require scrolling. Otherwise, `false`                                                                                                                                              | `false`   |
| `hideFooter`  | `true` if you want to hide the **footer** that displays a progress bar and navigation buttons. Otherwise, `false`.                                                                                                                                                                     | `false`   |
| `opacity`     | Background opacity. Valid values include any integer between `0` (completely transparent) and `100` (completely opaque). Note that this isn't the same as the CSS opacity scale (0-1).<br />_Valid only for widget mode option_                                                        | `100`     |
| `buttonText`  | Text to display in the "Start" button. Displayed only on touch-screen and mobile devices.<br />_Valid only for widget mode option_                                                                                                                                                     | `"Start"` |
| `mode`        | Identifies how the popup should behave. Valid values are `popup` (full-screen popup), `drawer_left` (popup slides in from the left), and `drawer_right` (popup slides in from the right).<br />_Popup mode option_                                                                     | `"popup"` |
| `autoOpen`    | `true` if the typeform should open automatically when the page loads. Otherwise, `false`.<br />_Popup mode option_                                                                                                                                                                     | `false`   |
| `autoClose`   | Time until the embedded typeform should automatically close after a respondent clicks the Submit button. Your typeform will automatically close after the time you specify, so respondents won’t have to manually close your typeform popup. In milliseconds.<br />_Popup mode option_ | `0`       |
| `onSubmit`    | Callback event that will execute immediately after a respondent successfully submits the typeform. <br />                                                                                                                                                                              | N/A       |
| `onReady`     | Callback event that will execute immediately when the form is loaded and displayed on screen. <br />                                                                                                                                                                                   | N/A       |

## Popup Mode Instance Methods

When **popup** is `true` but **autoOpen** is `false`, we can delegate to another
component the action to trigger the modal. The methods to be used are
`typeformPopup.open()` and `typeformPopup.close()`. An example to use them:

```html
<script>
    let typeformPopup;
</script>

<Typeform
    bind:typeformPopup
    popup
    autoOpen="{false}"
    url="https://mypersonalurl.typeform.com/to/1234"
/>

<button on:click={() => typeformPopup.open()}>Open</button>
```

### License

Code released under the [MIT license](LICENSE.md).
