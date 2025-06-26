<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
<a href="/dynamicforms">DynamicForms</a>
<a href="/snippets_training">SnippetsTraining</a>

<script lang="ts">
    import Simplecomponnent from './simple_componnent.svelte';

    type ButtonState = 'Positive' | 'Negative' | 'Neutral';
    let mybuttonstate: ButtonState = 'Neutral';
    let mysecondpropertyvalue: number | undefined = undefined;

    // Function to toggle state and update mysecondpropertyvalue
    function statechanger() {
        if (mybuttonstate === 'Positive') mybuttonstate = 'Negative';
        else if (mybuttonstate === 'Negative') mybuttonstate = 'Neutral';
        else mybuttonstate = 'Positive';
        val_adder();
    }

    // Function to set mysecondpropertyvalue based on state
    function val_adder() {
        if (mybuttonstate === 'Positive') {
            mysecondpropertyvalue = Math.floor(Math.random() * Number.MAX_SAFE_INTEGER) + 1;
        } else if (mybuttonstate === 'Negative') {
            mysecondpropertyvalue = Math.floor(Math.random() * Number.MAX_SAFE_INTEGER) - 1;
        } else {
            mysecondpropertyvalue = undefined; // Set to undefined for Neutral state
        }
    }

    // Reactive object to control props passed to Simplecomponnent
    $: componentProps = {
        myproperty: 'testerval',
        ...(mysecondpropertyvalue !== undefined ? { mysecondproperty: mysecondpropertyvalue } : {})
    };
</script>

<div>
    <h2>Simple Component Example</h2>
    <Simplecomponnent {...componentProps} />
    <button on:click={statechanger}>
        Click Me: Current State Is {mybuttonstate}
    </button>
</div>

<style>
    h1 {
        color: #ff3e00;
    }
    p {
        font-size: 1.2em;
    }
    a {
        color: #007acc;
        text-decoration: none;
    }
    a:hover {
        text-decoration: underline;
    }
</style>