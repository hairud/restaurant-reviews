<script lang="ts">
  type ButtonVariant = "red" | "white";

  export let text;
  export let onClick: () => void;
  export let type: ButtonVariant;
</script>

<button data-type={type === "red" ? "red" : "white"} on:click={onClick}>{text}</button>

<style>
  button {
    color: #ffffff;
    text-align: center;
    padding: 10px 30px;
    border-radius: 0;
  }

  button[data-type="red"] {
    border: 2px solid #ff5126;
    background-color: #ff5126;
  }

  button[data-type="white"] {
    border: 2px solid #fff;
    background-color: transparent;
  }

  button:hover {
    cursor: pointer;
  }

  button[data-type="red"]:hover {
    background-color: #ff3a09;
    color: #e6e6e6;
  }

  button[data-type="white"]:hover {
    border-color: #e6e6e6;
    color: #e6e6e6;
  }
</style>
