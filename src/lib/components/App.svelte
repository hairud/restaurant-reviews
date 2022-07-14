<script lang="ts">
  import Banner from "./Banner.svelte";
</script>

<div class="content">
  <Banner />
</div>

<style>
  .content {
    max-width: 1200px;
    margin: auto;
  }

  :global(body) {
    margin: 0px;
    font-family: Open Sans, sans-serif;
  }
</style>
