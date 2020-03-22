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
  import Card from "../../components/Card.svelte";
</script>

<style>
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

  @media (max-width: 1366px) {
    h1 {
      font-size: 5em;
    }
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 4em;
    }
  }

  @media (max-width: 420px) {
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
  /*===============================*/
  .cards {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin-top: 1.5em;
  }

  img {
    width: 100%;
    height: auto;
    max-height: 200px;
  }

  h2,
  h1,
  p {
    text-align: center;
    padding: 0.5em;
  }

  @media (max-width: 768px) {
    h2 {
      font-size: 1.5em;
    }
  }

  @media (max-width: 420px) {
    .cards {
      flex-direction: column;
    }
  }
</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Hírek, információk</h1>
    <h3>
      Hírek, információk, tudnivalók Balassagyarmat és környéke lakosságának a
      COVID-19 világjárvánnyal kapcsolatban.
    </h3>
  </div>
</div>

<section>
  <div class="cards">
    {#each posts as post}
      <!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
      <Card>
        <a rel="prefetch" href="blog/{post.slug}" slot="logo">
          <img alt="corona logo" src={post.thumbnail} />
          <h2>{post.title}</h2>
          <p>Közzétéve: {moment(post.date).format('ll')}</p>
        </a>
      </Card>
    {/each}
  </div>
</section>
