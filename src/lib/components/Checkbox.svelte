<script>
  export let checked = false;
  export let label = '';
  export let id = '';
</script>

<div>
  <input
    type="checkbox"
    id={id}
    checked={checked}
    on:change={() => checked = !checked}
  />
  <label for={id}>{label}</label>
</div>

<style>
  label {
    margin-left: 0.5em;
  }
</style>
