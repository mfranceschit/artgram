<script>
  import Header from "../components/Header";
  export let segment;
</script>

<Header {segment} />

<main>
  <slot />
</main>
