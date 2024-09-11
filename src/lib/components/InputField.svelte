<script>
  export let value = '';
  export let placeholder = '';
  export let id = '';
  export let name = '';
  export let error = '';
</script>

<div>
  <input
    type="text" 
    bind:value
    placeholder={placeholder}
    id={id}
    name={name}
  />
  {#if error}
    <span class="error-message">{error}</span>
  {/if}
</div>

<style>
  .error-message {
    color: red;
    font-size: 0.875em;
  }
</style>
