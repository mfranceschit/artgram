<script>
  import { onMount } from "svelte";

  import Header from "../components/Header";
  import Main from "../components/Main/Main";
  import Sidebar from "../components/Sidebar";
  import TimeLine from "../components/TimeLine";

  const objects = [100, 102, 104, 106, 108, 110, 112, 114, 116, 400];
  const BASE_API =
    "https://collectionapi.metmuseum.org/public/collection/v1/objects/";
  let posts = [];

  onMount(async () => {
    const museumRequest = objects.map(
      (objectId) =>
        new Promise(async (resolve, reject) => {
          const response = await fetch(`${BASE_API}${objectId}`);

          if (response.error) {
            reject(response.error);
          }

          const data = await response.json();
          resolve(data);
        })
    );
    const museumData = await Promise.allSettled(museumRequest);
    const results = museumData
      .filter((rawData) => rawData.status === "fulfilled")
      .map((data) => data.value);

    posts = results;
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
