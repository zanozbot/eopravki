<script>
  export let value;
  export let prop;
  export let label;
  export let placeholder;
  export let schema;
  export let icon;
  let isDirty = false;

  $: isPropValid = function() {
    const field = {};
    field[prop] = value;

    try {
      schema.validateSyncAt(prop, field);
      return true;
    } catch (e) {
      return false;
    }
  };

  $: isDirty = value != null;
</script>

<div class="field">
  <label for="name">{label}</label>
  <div class="control has-icons-left has-icons-right">
    <input
      class="input"
      class:is-danger={!isPropValid() && isDirty}
      type="text"
      id={prop}
      name={prop}
      bind:value
      {placeholder} />
    <span class="icon is-small is-left">
      <i class="fas fa-{icon}" />
    </span>
    {#if isPropValid()}
      <span class="icon is-small is-right">
        <i class="fas fa-check has-text-info" />
      </span>
    {/if}
  </div>
</div>
