<script>

</script>

<style lang="scss">
  @import "./styles/theme.scss";

  .line {
    width: 5rem;
    margin-top: 1rem;
    margin-right: 2rem;
    height: 8px;
    background: $primary-light;
  }

  @media (max-width: 1023px) {
    .explain-content {
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
      <div class="is-flex explain-content">
        <div class="bubble bottom-right primary" />
        <div class="line" />
        <div>
          <h1 class="title main-secondary-text-long">
            Vi ostanete doma, mi poskrbimo da bo hladilnik poln in opravki
            zaključeni.
          </h1>
          <div class="has-text-grey main-secondary-text-long">
            S kvalificiranim osebjem vam zagotovimo hiter obisk trgovine,
            lekarne, ... ali opravljanje različnih opravkov, kot so vračila
            knjig in razni prevzemi. Vse iz udobja vašega doma.
          </div>
          <div class="has-text-grey main-secondary-text-long">
            Enostavno sporočite vaše želje in mi jih izpolnimo.
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
