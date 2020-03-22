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
  div {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  h2,
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
    div {
      flex-direction: column;
    }
  }
</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>

<section>
  <div>
    {#each posts as post}
      <!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
      <Card>
        <a rel="prefetch" href="blog/{post.slug}" slot="name">
          <h2>{post.title}</h2>
        </a>
        <p slot="number">Közzétéve: {moment(post.date).format('ll')}</p>
      </Card>
    {/each}
  </div>
</section>
