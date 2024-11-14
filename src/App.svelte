<script lang="ts">
  import { theme } from "./lib/utils/store";
  import { register, init, locale } from "svelte-i18n";
  import { addMessages } from "svelte-i18n";

  import en from "./lib/i18n/en.json";
  import nl from "./lib/i18n/nl.json";

  // unlikely that I'll add other locales and don't feel like dealing with arrays and vite warnings
  addMessages("en", en);
  addMessages("nl", nl);

  let menuBarHeight = "2em";

  init({
    fallbackLocale: "en",
    initialLocale: "en",
  });
</script>

<div
  class="wrapper"
  style="--fontColor: {$theme.fontColor};
  --backgroundColor: {$theme.backgroundColor};
  --linkColor: {$theme.linkColor};
  --fadedBackgroundColor: {$theme.fadedBackgroundColor};
  --highlightColor: {$theme.highlightColor}"
>
  <MenuBar {menuBarHeight} />

  <main style="--menu-bar-height:{menuBarHeight}">
    <Landing />
    <Intro />
    <Data />
    <Showcase />
    <Blog />
    <Skill />
  </main>
  <Footer />
</div>

<style>
  .wrapper {
    margin: 0;
    color: var(--fontColor);
    background-color: var(--backgroundColor);
  }
  main {
    display: flex;
    flex-direction: column;
    width: 80vw;
    margin: auto;
  }
  :global(a) {
    color: var(--linkColor);
  }
  :global(:root) {
    --fontSize: 24px;
    --fontWeight: 400;
  }
</style>
