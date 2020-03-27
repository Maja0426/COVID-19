<script context="module">
  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`_posts/${params.slug}.md`);

    if (res.status === 200) {
      return { postMd: await res.text() };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  import fm from "front-matter";
  import MarkdownIt from "markdown-it";
  import moment from "moment";
  import "moment/locale/hu";
  import { stores } from "@sapper/app";

  const { page } = stores();
  const { slug } = $page.params;

  export let postMd;

  const md = new MarkdownIt();

  $: frontMatter = fm(postMd);
  $: post = {
    ...frontMatter.attributes,
    html: md.render(frontMatter.body)
  };
</script>

<style>
  /*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
  h1 {
    text-align: center;
    font-size: 2.5em;
    margin-top: 1.5em;
  }

  /* .date {
    width: 100%;
  } */

  .img-bar {
    display: flex;
    width: 100%;
    background: #000;
  }

  .img-text {
    display: flex;
    width: 80%;
  }

  /*   .fb-share-button {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    width: 20%;
    padding-right: 1em;
  }
 */
  h5 {
    width: inherit;
    padding: 1em;
    background: #000;
    color: #fff;
  }

  .content {
    margin-top: 4em;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .back button {
    margin: auto;
    margin-top: 1em;
  }

  .content :global(p > img) {
    margin: auto;
    display: flex;
    justify-content: center;
    width: 50%;
  }

  section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .thumbnail img {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  .content :global(h2) {
    font-size: 1.4em;
    font-weight: 500;
  }

  .content :global(pre) {
    background-color: #f9f9f9;
    box-shadow: inset 1px 1px 5px rgba(0, 0, 0, 0.05);
    padding: 0.5em;
    border-radius: 2px;
    overflow-x: auto;
  }

  .content :global(pre) :global(code) {
    background-color: transparent;
    padding: 0;
  }

  .content :global(ul) {
    line-height: 1.5;
  }

  .content :global(li) {
    margin: 0 0 0.5em 0;
  }

  @media (max-width: 420px) {
    .content :global(p > img) {
      width: 85%;
    }
    .first-h2 {
      font-size: 2em;
    }
  }
</style>

<svelte:head>
  <title>{post.title}</title>
  <!-- Load Facebook SDK for JavaScript -->
  <script>
    (function(d, s, id) {
      var js,
        fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s);
      js.id = id;
      js.src = "https://connect.facebook.net/en_US/sdk.js#xfbml=1&version=v3.0";
      fjs.parentNode.insertBefore(js, fjs);
    })(document, "script", "facebook-jssdk");
  </script>
</svelte:head>

<section>
  <div id="fb-root" />
  <h1 class="first-h2">{post.title}</h1>
  <div class="thumbnail">
    <img src={post.thumbnail} alt={post.title} />
    <div class="img-bar">
      <div class="img-text">
        <h5>
          Közzétéve: {moment(post.date).format('lll')}
          <br />
          Szerző: {post.name}
        </h5>
      </div>
      <div
        class="fb-share-button"
        data-href="https://bgykaranten.hu/blog/{slug}"
        data-layout="button"
        data-size="small" />
    </div>
  </div>
  <div class="content">
    {@html post.html}
  </div>

  <div class="back">
    <a href="/blog">
      <button>Előző oldal</button>
    </a>
  </div>
</section>
