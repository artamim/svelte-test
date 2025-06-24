<script lang="ts">
  let content = $state('');
</script>

<div class="card">
  <!-- Card content goes here -->
  <slot />
</div>

<textarea bind:value={content}></textarea>
<div>Content Value: {content}</div>
<style>
  .card {
    border: 1px solid #ccc;
    padding: 20px;
    border-radius: 8px;
  }
</style>