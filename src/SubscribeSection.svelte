<script>
  import { isModalActive } from "./store.js";
  import Input from "./Input.svelte";
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

  $: isFormValid = schema.isValidSync({ email, name, area, agreement });

  async function openModal() {
    isModalActive.set(true);

    const apiRoot =
      "https://gmail.us19.list-manage.com/subscribe/post-json?u=9a49a5665462feee8b6f877e4&amp;id=d8f1f5d1e5";

    const apiURL = `${apiRoot}&EMAIL=${email}&FNAME=${name}&LNAME=${area}&c=?`;

    const response = await fetch(apiURL, {
      method: "POST",
      mode: "no-cors",
      cache: "no-cache",
      credentials: "same-origin",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json"
      }
    });

    name = "";
    email = "";
    area = areas[0];
    agreement = false;
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

  .end-of-content {
    margin-bottom: 2rem;
  }

  .select::after {
    border-color: $info;
  }

  button {
    margin-top: 1.25rem;
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

<section id="prijava" class="section">
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
            Po prijavi vam sporočimo takoj, ko bodo storitve eOpravkov
            funkcionalne.
          </div>

          <Input
            {schema}
            label="Elektronska pošta"
            placeholder="Vnesite elektronsko pošto"
            bind:value={email}
            icon="envelope"
            prop="email"
            name="EMAIL"
            id="mce-EMAIL" />

          <Input
            {schema}
            label="Ime in priimek"
            placeholder="Vnesite ime in priimek"
            bind:value={name}
            icon="user"
            prop="name"
            name="FNAME"
            id="mce-FNAME" />

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

          <div class="field">
            <label class="checkbox main-secondary-text-long has-text-grey">
              <input
                type="checkbox"
                name="agreement"
                bind:checked={agreement} />
              Strinjam se, da lahko na vpisan email naslov prejemam eOpravki
              novice, obvestila, članke in posebne ponudbe.
            </label>
          </div>

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
