<script>
  import Main from "../components/Main";
  export let status;
  export let error;

  const dev = process.env.NODE_ENV === "development";
</script>

<svelte:head>
  <title>{status}</title>
</svelte:head>

<Main>
  <div class="Error">
    <h1>{status}</h1>
    <p>{error.message}</p>
    {#if dev && error.stack}
      <pre>{error.stack}</pre>
    {/if}
  </div>
</Main>

<style>
  .Error {
    padding: 4em 0 0 0;
  }

  h1,
  p {
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }
</style>
