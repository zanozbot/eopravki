<script>
  import { isModalActive } from "./store.js";

  function closeModal() {
    isModalActive.set(false);
  }
</script>

<style lang="scss">
  @import "./styles/theme.scss";
  .section {
    padding: 3rem;
    border-radius: $border-radius * 2;
  }
  @media (max-width: 1023px) {
    .modal-content {
      width: 90%;
    }
  }
  .image {
    margin-top: 2rem;
    display: flex;
    justify-content: center;
    img {
      max-width: 300px;
    }
  }
</style>

<div class="modal" class:is-active={$isModalActive}>
  <div class="modal-background" on:click={closeModal} />
  <div class="modal-content">

    <section class="section has-background-white">
      <h1 class="title main-secondary-text-long">Hvala za vaš interes.</h1>
      <div class="has-text-grey main-secondary-text-long end-of-content">
        Prejeli smo vaše zanimanje za storitev eOpravki. Sporočili vam bomo
        takoj, ko bo naročanje preko eDostave mogoče.
      </div>

      <figure class="image">
        <img src="images/confirmed.svg" alt="Prijava oddana" />
      </figure>

    </section>

  </div>
  <button
    on:click={closeModal}
    class="modal-close is-large"
    aria-label="close" />
</div>
