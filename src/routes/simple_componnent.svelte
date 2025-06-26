<script lang="ts">
    let count = $state(0)
    let {
        myproperty,
        mysecondproperty
    }: {
        myproperty: string;
        mysecondproperty?: number;
    } = $props()
</script>
<h1>Simple Component</h1>
<p>This is a simple Svelte component demonstrating state management.</p>
<button onclick={() => count += 1}>
    Count {count} 
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