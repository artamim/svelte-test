<!-- src/routes/+page.svelte -->
<script lang="ts">
  import Card from '$lib/Card.svelte';
  import Counter from '$lib/Counter.svelte';

  let activeTab = $state('card'); // Use $state for reactive state

  function setTab(tab: 'card' | 'counter') {
    activeTab = tab; // Assign to the $state proxy
  }
</script>

<nav>
  <button onclick={() => setTab('card')}>Card</button>
  <button onclick={() => setTab('counter')}>Counter</button>
</nav>

{#if activeTab === 'card'}
  <Card>
    <h2>Welcome to the Homepage</h2>
    <p>This is the card component displayed at the homepage.</p>
  </Card>
{:else if activeTab === 'counter'}
  <Counter cusvalue="Tamim" />
{/if}