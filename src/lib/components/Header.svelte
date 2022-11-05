<script lang="ts">
  import logo from "../assets/logo.png";
</script>

<header>
  <div class="header-content">
    <a href="/">
      <img src={logo} alt="Air ballon logo" />
      Travel tours
    </a>
  </div>
</header>

<style>
  header {
    box-shadow: 0 0 5px rgb(230, 230, 230);
    display: flex;
    flex-direction: row;
    height: 40px;
    padding: 5px;
    align-items: center;
    font-weight: 600;
    text-transform: uppercase;
    margin-bottom: 24px;
  }

  a {
    display: flex;
    flex-direction: row;
    align-items: center;
    height: 40px;
    text-decoration: none;
    color: inherit;
  }

  img {
    max-height: 100%;
  }

  .header-content {
    width: 1200px;
    margin: auto;
  }
</style>
