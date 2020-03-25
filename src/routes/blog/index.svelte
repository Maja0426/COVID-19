<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`blog.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
  import moment from "moment";
  import "moment/locale/hu";
  import { onMount, onDestroy } from "svelte";
  import Card from "../../components/Card.svelte";

  const loaded = new Map();
  let visible = false;

  function lazy(node, data) {
    if (loaded.has(data.src)) {
      node.setAttribute("src", data.src);
    } else {
      // simulate slow loading network
      setTimeout(() => {
        const img = new Image();
        img.src = data.src;
        img.onload = () => {
          loaded.set(data.src, img);
          node.setAttribute("src", data.src);
        };
      }, 50);
    }

    return {
      destroy() {}
    };
  }

  onMount(() => {
    visible = true;
  });

  onDestroy(() => {
    visible = false;
  });
</script>

<style>
  section {
    display: flex;
    padding: 4em 10%;
    flex-wrap: wrap;
  }

  h1 {
    font-size: 6em;
    text-align: center;
    margin: 0 auto 0.5em;
    font-weight: 400;
    color: #fff;
  }

  .main-title-hero h3 {
    color: #fff;
    text-align: center;
    font-size: 1.7em;
    font-weight: 300;
    text-transform: uppercase;
  }

  .main-bg-hero {
    background: url("../img/news.jpg") no-repeat center/cover;
  }

  .wrapper {
    display: flex;
  }

  .cards {
    width: 45%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin: 1em;
  }

  .body {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-width: 200px;
    background: #000;
    color: #fff;
    padding: 0.3em;
  }

  .image,
  .body {
    display: flex;
    flex-direction: column;
  }

  img {
    min-width: 100px;
    width: 100%;
    height: 250px;
    object-fit: cover;
  }

  h3,
  h1 {
    text-align: center;
    padding: 0.5em;
  }

  p {
    margin: 0;
    text-align: center;
  }

  @media (max-width: 1366px) {
    h1 {
      font-size: 5em;
    }
  }

  @media (max-width: 768px) {
    section {
      padding: 4em 2em;
    }
    .wrapper {
      flex-direction: column;
    }
    .cards {
      width: 100%;
      margin: 1em 0;
    }

    .body {
      padding: 0;
    }

    h1 {
      font-size: 4em;
    }
    h3 {
      font-size: 1.5em;
    }
  }

  @media (max-width: 420px) {
    section {
      padding: 4em 1.5em;
    }
    h3 {
      font-size: 16px;
    }

    .main-title-hero h3 {
      font-size: 1.2em;
    }

    h1 {
      font-size: 3.5em;
    }
  }

  @media (max-width: 320px) {
    h1 {
      font-size: 3em;
    }
  }
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Blog</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Hírek, infók</h1>
    <h3>
      Hírek, információk, tudnivalók Balassagyarmat és környéke lakosságának a
      COVID-19 világjárvánnyal kapcsolatban.
    </h3>
  </div>
</div>

<section>
  {#each posts as post}
    <div class="cards">
      <a rel="prefetch" href="blog/{post.slug}">
        <div class="wrapper">
          <div class="image">
            <img alt={post.title} use:lazy={{ src: post.thumbnail }} />
          </div>
          <div class="body">
            <h3>{post.title}</h3>
            <p>Közzétéve: {moment(post.date).format('ll')}</p>
          </div>
        </div>
      </a>
    </div>
  {/each}
</section>
