<script>

  let count = $state(0); // Use $state to create a reactive state variable
  // $state is a Svelte-specific feature to create reactive state variables
  let doubled = $derived(count * 2); // Use $derived to create a derived state based on count
  // $derived is a Svelte-specific feature to create reactive derived values
  let { cusvalue } = $props(); //Use $props to get props in Svelte

  $effect(() => {
    console.log(`Count changed to ${count}`);
  });

  function increment() {
    count += 1;
  }
</script>

<button onclick={increment}>
  Count: {count}, Doubled: {doubled}, Custom Value: {cusvalue}
</button>