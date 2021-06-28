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

<Main>
  <TimeLine {posts} />
  <Sidebar />
</Main>
