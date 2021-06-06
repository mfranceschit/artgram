<script>
  import App from "../../containers/App.svelte";
  import Card from "../Card";
  export let posts = [];
</script>

<div class="TimeLine">
  <div class="TimeLine-container">
    {#each posts as post}
      <Card {...post} />
    {:else}
      <p>Loading</p>
    {/each}
  </div>
</div>

<style>
  .TimeLine {
    padding: 4em 0 0 0;
  }
</style>
