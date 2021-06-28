<script context="module">
  const BASE_API = "https://rickandmortyapi.com/api/character";

  export async function preload() {
    let data = {};

    const response = await this.fetch(`${BASE_API}`);
    data = await response.json();

    return { posts: data.results };
  }
</script>

<script>
  import Main from "../components/Main/Main";
  import Sidebar from "../components/Sidebar";
  import TimeLine from "../components/TimeLine";

  export let posts = [];
</script>

<svelte:head>
  <title>Sveltegram</title>
</svelte:head>

<Main>
  <TimeLine {posts} />
  <Sidebar />
</Main>
