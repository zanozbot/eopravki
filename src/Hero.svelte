<script>

</script>

<style lang="scss">
  @import "./styles/theme.scss";

  .hero-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-column-gap: 1rem;
    align-items: center;
  }

  .hero-items {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 1rem;
  }

  .main-secondary-text {
    max-width: 30rem;
    margin-bottom: 2rem;
  }

  .hero-item {
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

  @media (min-width: 1215px) {
    .hero-items {
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    }
  }

  @media (max-width: 1023px) {
    .hero-grid {
      grid-template-columns: none;
    }

    .hero-items {
      margin-top: 3rem;
    }
  }
</style>

<section class="section">
  <div class="container">

    <div class="hero-grid">
      <div class="hero-content">
        <h1 class="title">
          Enostavno po opravkih,
          <br />
          kar
          <span class="is-highlighted-info">od doma</span>
        </h1>
        <div class="has-text-grey has-margin-bottom-2rem main-secondary-text">
          Ko nimate časa, ste utrujeni ali enostavno želite ostati več časa doma
          z družino vam priskočimo na pomoč.
        </div>
        <button class="button is-link is-info is-rounded has-text-weight-bold">
          Prijavite se →
        </button>
      </div>

      <div class="hero-items">
        <div class="hero-item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-shopping-cart fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Živila</h3>
          <div class="has-text-grey">
            Obisk trgovine in nakup željenih izdelkov
          </div>
        </div>

        <div class="hero-item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-pills fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Zdravila</h3>
          <div class="has-text-grey">
            Obisk lekarne in nakup zdravil brez recepta
          </div>
        </div>

        <div class="hero-item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-book fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Knjižnjica</h3>
          <div class="has-text-grey">
            Vrnitev ali izposoja knjige na vašo kartico
          </div>
        </div>

        <div class="hero-item">
          <span class="icon is-large has-text-info">
            <i class="fas fa-random fa-2x" />
          </span>
          <h3 class="title is-size-5 is-uppercase">Ostalo</h3>
          <div class="has-text-grey">
            Razni ostali opravki, ki jih potrebujete
          </div>
        </div>
      </div>

    </div>
  </div>
</section>
