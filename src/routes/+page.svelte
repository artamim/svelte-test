<!-- src/routes/+page.svelte -->
<script>
  import Card from '$lib/Card.svelte';
</script>

<nav>
  <a href="/">Home</a>
  <a href="/counter">Counter</a>
</nav>

<Card>
  <h2>Welcome to the Homepage</h2>
  <p>This is the card component displayed at the homepage.</p>
</Card>