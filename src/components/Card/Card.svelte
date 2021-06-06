<script>
  import { blur } from "svelte/transition";

  import Comments from "../Comments";
  import Modal from "../Modal";
  import Share from "../Share";

  export let country;
  export let primaryImage;
  export let primaryImageSmall;
  export let creditLine;
  export let title;
  export let department;
  export let comments = [];

  let openModal = false;

  const handleModal = () => {
    openModal = !openModal;
  };
</script>

<div class="Card">
  {#if openModal}
    <div transition:blur>
      <Modal>
        <Share on:click={handleModal} />
      </Modal>
    </div>
  {/if}
  <div class="Card-container">
    <div class="Card-header">
      <div class="Card-user">
        <img src={primaryImageSmall} alt="Most wanted" />
        <h2>
          {department}
          <span>{country}</span>
        </h2>
      </div>
      <div class="Card-settings">
        <i class="fas fa-ellipsis-h" />
      </div>
    </div>
    <div class="Card-photo">
      <figure>
        <img src={primaryImage} alt={title} />
      </figure>
    </div>
    <div class="Card-icons">
      <div class="Card-icons-left">
        <i class="fas fa-heart" />
        <i class="fas fa-paper-plane" on:click={handleModal} />
      </div>
      <div class="Card-icons-right">
        <i class="fas fa-bookmark" />
      </div>
    </div>
    <div class="Card-description">
      <h3>{title}</h3>
      <span>{creditLine}</span>
    </div>
    <Comments {comments} />
  </div>
</div>

<style>
  .Card {
    border: 1px solid rgba(219, 219, 219, 1);
    border-radius: 4px;
    background-color: white;
    margin: 0 0 2em 0;
  }
  .Card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1em;
  }
  .Card-user {
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }
  .Card-user img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }
  .Card-user h2 {
    margin: 0;
    padding: 0;
    font-size: 14px;
    font-weight: 600;
    margin: 0 0 0 1em;
    color: black;
  }
  .Card-user h2 span {
    display: block;
    font-size: 12px;
    font-weight: normal;
    color: rgba(38, 38, 38, 0.7);
  }
  .Card-photo {
    padding: 0;
    margin: 0;
  }
  .Card-photo img {
    width: 100%;
    height: auto;
  }
  .Card-photo figure {
    margin: 0;
    padding: 0;
    cursor: pointer;
  }
  .Card-settings i {
    cursor: pointer;
  }
  .Card-icons {
    padding: 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .Card-icons i {
    margin: 0 1em 0 0;
    cursor: pointer;
    font-size: 20px;
  }
  .Card-icons i:last-child {
    margin: 0;
  }
  .Card-description {
    padding: 0 1em 1em 1em;
  }
  .Card-description h3 {
    font-size: 14px;
    font-weight: bold;
    color: black;
  }
  .Card-description span {
    font-size: 14px;
  }
  .active-like {
    color: #bc1888;
    animation: bounce linear 0.8s;
    animation-iteration-count: 1;
    transform-origin: 20% 20%;
  }
  .active-bookmark {
    color: #f09433;
  }

  @keyframes bounce {
    0% {
      transform: translate(0px, 0px);
    }
    15% {
      transform: translate(0px, -25px);
    }
    30% {
      transform: translate(0px, 0px);
    }
    45% {
      transform: translate(0px, -15px);
    }
    60% {
      transform: translate(0px, 0px);
    }
    75% {
      transform: translate(0px, -5px);
    }
    100% {
      transform: translate(0px, 0px);
    }
  }
</style>
