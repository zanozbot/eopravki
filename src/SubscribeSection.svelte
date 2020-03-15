<script>
  import { isModalActive } from "./store.js";
  import { createForm } from "svelte-forms-lib";
  import * as yup from "yup";

  let areas = [
    "Gorenjska",
    "Goriška",
    "Jugovzhodna Slovenija",
    "Koroška",
    "Obalno-kraška",
    "Osrednjeslovenska",
    "Podravska",
    "Pomurska",
    "Posavska",
    "Primorsko-notranjska",
    "Savinjska",
    "Zasavska"
  ];

  let email;
  let name;
  let area = areas[1];
  let agreement;

  const schema = yup.object().shape({
    email: yup
      .string()
      .required()
      .email(),
    name: yup
      .string()
      .min(6)
      .required(),
    area: yup.string().required(),
    agreement: yup
      .boolean()
      .required()
      .oneOf([true])
  });

  const isDirty = {};

  $: isFormValid = schema.isValidSync({ email, name, area, agreement });
  $: isPropValid = function(prop, value) {
    try {
      schema.validateSyncAt(prop, value);
      return true;
    } catch (e) {
      return false;
    }
  };

  function openModal() {
    isModalActive.set(true);
  }

  function markAsDirty(prop, value) {
    if (value != null) {
      isDirty[prop] = true;
    }
  }
</script>

<style lang="scss">
  @import "./styles/theme.scss";

  .line {
    width: 5rem;
    margin-top: 1rem;
    margin-right: 2rem;
    height: 8px;
    background: $info-light;
  }

  .control {
    margin-bottom: 1.5rem;

    .select,
    select {
      width: 100%;
    }

    .input,
    .select,
    .icon,
    select {
      height: 3rem;
    }
  }

  .select::after {
    border-color: $info;
  }

  .end-of-content {
    margin-bottom: 2rem;
  }

  label {
    margin-bottom: 0.25rem;
    display: block;
  }

  button {
    margin-top: 2rem;
  }

  @media (max-width: 1023px) {
    .subscribe-content {
      flex-direction: column;
      .line {
        margin-bottom: 0.5rem;
      }
    }
  }
</style>

<section class="section">
  <div class="container">
    <div class="content-grid">
      <div class="is-flex subscribe-content">
        <div class="bubble bottom-middle info" />
        <div class="line" />
        <div>
          <h1 class="title main-secondary-text-long">
            Prijavite se in ne izgubljajte več časa z nepotrebnimi opravki.
          </h1>
          <div class="has-text-grey main-secondary-text-long end-of-content">
            Po prijavi vam sporočimo takoj, ko bodo storitve eDostave
            funkcionalne.
          </div>

          <label for="email">Elektronska pošta</label>
          <div class="control has-icons-left has-icons-right">
            <input
              class="input"
              class:is-danger={!isPropValid('email', {
                email
              }) && isDirty['email']}
              on:change={markAsDirty('email', email)}
              type="email"
              id="email"
              name="email"
              bind:value={email}
              placeholder="Vnesite elektronsko pošto" />
            <span class="icon is-small is-left">
              <i class="fas fa-envelope" />
            </span>
            {#if isPropValid('email', { email })}
              <span class="icon is-small is-right">
                <i class="fas fa-check has-text-info" />
              </span>
            {/if}
          </div>

          <label for="name">Ime in priimek</label>
          <div class="control has-icons-left has-icons-right">
            <input
              class="input"
              class:is-danger={!isPropValid('name', {
                name
              }) && isDirty['name']}
              type="text"
              on:change={markAsDirty('name', name)}
              id="name"
              name="name"
              bind:value={name}
              placeholder="Vnesite ime in priimek" />
            <span class="icon is-small is-left">
              <i class="fas fa-user" />
            </span>
            {#if isPropValid('name', { name })}
              <span class="icon is-small is-right">
                <i class="fas fa-check has-text-info" />
              </span>
            {/if}
          </div>

          <label for="area">Lokacija</label>
          <div class="field">
            <div class="control has-icons-left">
              <div class="select">
                <select id="area" name="area" bind:value={area}>
                  {#each areas as area}
                    <option value={area}>{area}</option>
                  {/each}
                </select>
              </div>
              <span class="icon is-small is-left">
                <i class="fas fa-map-marker-alt" />
              </span>
            </div>
          </div>

          <label class="checkbox main-secondary-text-long has-text-grey">
            <input type="checkbox" name="agreement" bind:checked={agreement} />
            Strinjam se, da lahko na vpisan email naslov prejemam eDostava
            novice, obvestila, članke in posebne ponudbe.
          </label>

          <button
            class="button is-link is-info has-text-weight-bold"
            disabled={!isFormValid}
            on:click={openModal}>
            Prijavite se →
          </button>

        </div>
      </div>
    </div>
  </div>
</section>
