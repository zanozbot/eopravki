<script>
  import Hero from "./Hero.svelte";
  import SafetySection from "./SafetySection.svelte";
  import ExplainSection from "./ExplainSection.svelte";
  import PriceSection from "./PriceSection.svelte";
  import SubscribeSection from "./SubscribeSection.svelte";
  import Footer from "./Footer.svelte";
  import Modal from "./Modal.svelte";
  import Header from "./Header.svelte";
</script>

<style global lang="scss">
  @import "./styles/global.scss";
</style>

<main>
  <Header />
  <Hero />
  <SafetySection />
  <ExplainSection />
  <PriceSection />
  <SubscribeSection />
  <Modal />
  <Footer />
</main>
