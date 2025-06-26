<script lang="ts">
    let count = $state(0)
    let incrval = $derived(count + 1)
    let {
        myproperty,
        mysecondproperty
    }: {
        myproperty: string;
        mysecondproperty?: number;
    } = $props()
    let incr_secondary_prop_val: number | undefined = $derived(
        mysecondproperty !== undefined ? mysecondproperty + 1 : undefined
    )
</script>
<h1>Simple Component</h1>
<p>This is a simple Svelte component demonstrating state management.</p>
<button onclick={() => count += 1}>
    Count {count} 
    Increment value {incrval}
    Secondary Property Incremented Value: {incr_secondary_prop_val !== undefined ? incr_secondary_prop_val : 'N/A'}
</button>
<div>
    {#if mysecondproperty !== undefined && mysecondproperty > 0}
        Secondary Value is {mysecondproperty}, but it is positive
    {:else if mysecondproperty !== undefined && mysecondproperty <= 0}
        Secondary Value is {mysecondproperty}, but it is not positive
    {:else}
        No secondary value provided
    {/if}
</div>
<div>Property value: {myproperty}</div>