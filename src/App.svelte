<script>
  import Hero from "./Hero.svelte";
  import SafetySection from "./SafetySection.svelte";
</script>

<style global lang="scss">
  @import "./styles/global.scss";
</style>

<header>
  <nav class="navbar container" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <span class="navbar-item has-text-info is-size-5 has-text-weight-bold">
        eDostava
      </span>
    </div>
  </nav>
</header>

<main>
  <Hero />
  <SafetySection />
</main>
