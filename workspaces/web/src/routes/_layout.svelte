<script context="module">
  import { waitLocale } from "svelte-i18n"
  import authStore from "../auth"

  export async function preload() {
    return waitLocale()
  }
</script>

<script>
  import settings from "../settings"
</script>

<svelte:head>

  <meta property="og:title" content="MazeLearn" />

</svelte:head>

{#if process.browser !== true || ($authStore.online === null && settings.features.authEnabled)}
  <div class="pageloader is-active">
    <span class="title">MazeLearn</span>
  </div>
{/if}

<main>
  <slot />
</main>
