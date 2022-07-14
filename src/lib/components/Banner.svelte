<script lang="ts">
  import background from "../assets/banner-background.jpeg";
  import crop from "../assets/crop.png";
  import balloon from "../assets/balloon.png";
  import Button from "./Button.svelte";
</script>

<div class="wrap">
  <img alt="banner-part" class="background" src={background} />
  <img alt="banner-part" class="crop" src={crop} />
  <img alt="banner-part" class="ballon" src={balloon} />
  <h4>it's time for great</h4>
  <h1>Adventure</h1>
  <div class="button-wrap">
    <Button text="start now" type="white" />
  </div>
</div>

<style>
  .wrap {
    width: 1131px;
    height: 736px;
    position: relative;
    overflow: hidden;
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  h4 {
    font-size: 20px;
    z-index: 4;
    color: #fff;
    font-weight: 300;
    margin: -70px 0px 0px;
  }

  h1 {
    font-size: 96px;
    font-weight: 400;
    z-index: 4;
    margin: 20px 0px;
    color: #fff;
  }

  .button-wrap {
    z-index: 4;
  }

  .crop {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
  }

  .background {
    left: 50%;
    max-width: 912px;
    position: absolute;
    margin: 13px auto 0px;
    transform: translateX(-50%);
  }

  .ballon {
    top: 53px;
    left: 162px;
    position: absolute;
    max-height: 289px;
    max-width: 228px;
  }
</style>
