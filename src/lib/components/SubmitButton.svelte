<script>
  export let text = 'Submit';
  export let onClick = () => {};
</script>

<button on:click={onClick}>
  {text}
</button>
