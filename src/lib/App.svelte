<script lang="ts">
  import { Router, Route } from "svelte-routing";

  import Header from "./components/Header.svelte";
  import Home from "./routes/Home.svelte";
  import Tours from "./routes/Tours.svelte";
</script>

<Header />
<div class="content">
  <Router>
    <Route path="/tours">
      <Tours />
    </Route>
    <Route path="/">
      <Home />
    </Route>
  </Router>
</div>

<style>
  .content {
    max-width: 1200px;
    margin: auto;
    min-height: 100vh;
  }

  :global(body) {
    margin: 0px;
    font-family: Open Sans, sans-serif;
  }
</style>
