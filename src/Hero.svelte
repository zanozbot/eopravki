<script>
  function scrollToSubscription() {
    document.getElementById("prijava").scrollIntoView({ behavior: "smooth" });
  }
</script>

<style lang="scss">
  @import "./styles/theme.scss";
  .items {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 1rem;
  }
  .button {
    margin-top: 2rem;
  }
  .item {
    background: $info-lighter;
    padding: 1.5rem;
    border-radius: $border-radius;
    .icon {
      margin-bottom: 0.5rem;
    }
    h3 {
      margin-bottom: 0.75rem !important;
    }
  }

  @media (max-width: 1023px) {
    .section {
      padding-top: 1.5rem;
    }
  }

  @media (min-width: 1215px) {
    .items {
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    }
  }
</style>

<section class="section">
  <div class="container">

    <div class="content-grid">
      <div class="content content-margin-bottom">
        <div class="bubble top-left info" />
        <h1 class="title">
          Enostavno po opravkih,
          <br />
          kar
          <span class="is-highlighted-info">od doma</span>
        </h1>
        <div
          class="has-text-grey has-margin-bottom-2rem main-secondary-text-short">
          Ko nimate časa, ste utrujeni ali enostavno želite ostati več časa doma
          z družino vam priskočimo na pomoč.
        </div>
        <button
          class="button is-link is-info has-text-weight-bold"
          on:click={scrollToSubscription}>
          Prijavite se →
        </button>
      </div>

      <div class="items">
        <div class="item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-shopping-cart fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Živila</h3>
          <div class="has-text-grey">
            Obisk trgovine in nakup željenih izdelkov
          </div>
        </div>

        <div class="item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-pills fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Zdravila</h3>
          <div class="has-text-grey">
            Obisk lekarne in nakup zdravil brez recepta
          </div>
        </div>

        <div class="item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-book fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Knjižnjica</h3>
          <div class="has-text-grey">
            Vrnitev ali izposoja knjige na vašo kartico
          </div>
        </div>

        <div class="item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-random fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Ostalo</h3>
          <div class="has-text-grey">
            Razni ostali opravki, ki jih potrebujete izvedene na daljavo
          </div>
        </div>
      </div>

    </div>
  </div>
</section>
