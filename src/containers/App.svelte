<script>
  import { onMount } from "svelte";

  import Header from "../components/Header";
  import Main from "../components/Main/Main";
  import Sidebar from "../components/Sidebar";
  import TimeLine from "../components/TimeLine";

  const BASE_API = "https://rickandmortyapi.com/api/character";
  let posts = [];

  onMount(async () => {
    try {
      const response = await fetch(`${BASE_API}`);
      const data = await response.json();
      posts = data.results;
      console.log(posts);
    } catch (error) {
      // TODO: Log error
    }
  });
</script>

<Header />
<Main>
  <TimeLine {posts} />
  <Sidebar />
</Main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap");
  @import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");
  :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
  }
  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>
