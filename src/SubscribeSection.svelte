<script>
  import { isModalActive } from "./store.js";

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

  function openModal() {
    isModalActive.set(true);
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
          <div class="control has-icons-left">
            <input
              class="input"
              type="email"
              id="email"
              placeholder="Vnesite elektronsko pošto" />
            <span class="icon is-small is-left">
              <i class="fas fa-envelope" />
            </span>
          </div>

          <label for="name">Ime in priimek</label>
          <div class="control has-icons-left">
            <input
              class="input"
              type="email"
              id="name"
              placeholder="Vnesite ime in priimek" />
            <span class="icon is-small is-left">
              <i class="fas fa-user" />
            </span>
          </div>

          <label for="area">Lokacija</label>
          <div class="field">
            <div class="control has-icons-left">
              <div class="select">
                <select id="area">
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
            <input type="checkbox" />
            Strinjam se, da lahko na vpisan email naslov prejemam eDostava
            novice, obvestila, članke in posebne ponudbe.
          </label>

          <button
            class="button is-link is-info has-text-weight-bold"
            on:click={openModal}>
            Prijavite se →
          </button>

        </div>
      </div>
    </div>
  </div>
</section>
