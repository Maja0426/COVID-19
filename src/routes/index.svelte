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
  import axios from "axios";
  import moment from "moment";
  import { onMount, onDestroy } from "svelte";

  import "moment/locale/hu";
  import Card from "../components/Card.svelte";

  export let posts;

  const covidHunUrl =
    "https://api.apify.com/v2/key-value-stores/RGEUeKe60NjU16Edo/records/LATEST?disableRedirect=true";
  const covidHUNCSSE = "https://covid19.mathdro.id/api/countries/hu";
  const covidGlobalUrl = "https://covid19.mathdro.id/api/";
  let confirmedGlobal, recoveredGlobal, deathsGlobal;
  let infectedHun, deceasedHun, recoveredHun, quarantinedHun, testedHun;
  let lastUpdateGlobal, lastUpdateHun;
  let isBlogs = false;

  $: if (posts.length >= 2) {
    isBlogs = true;
  }

  const loaded = new Map();
  let visible = false;

  onMount(() => {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", user => {
        if (!user) {
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        }
      });
    }
  });

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

  onMount(async function getData() {
    try {
      const responseHun = await axios.get(covidHunUrl);
      quarantinedHun = responseHun.data.quarantined;
      testedHun = responseHun.data.tested;
      infectedHun = responseHun.data.infected;
      recoveredHun = responseHun.data.recovered;

      const responseHUNCSSE = await axios.get(covidHUNCSSE);
      deceasedHun = responseHUNCSSE.data.deaths.value;
      lastUpdateHun = responseHun.data.lastUpdatedAtApify;

      const responseGlobal = await axios.get(covidGlobalUrl);
      confirmedGlobal = responseGlobal.data.confirmed.value;
      recoveredGlobal = responseGlobal.data.recovered.value;
      deathsGlobal = responseGlobal.data.deaths.value;
      lastUpdateGlobal = responseGlobal.data.lastUpdate;
    } catch (error) {
      console.log(error);
    }
  });
</script>

<style>
  .main-bg-hero {
    background: url(".././img/covid-wallpaper.png") no-repeat 10% center/cover;
  }

  .main-title-hero h3 {
    color: #fff;
    text-align: center;
    font-size: 1.7em;
    font-weight: 300;
    text-transform: uppercase;
  }

  h1 {
    font-size: 6em;
    text-align: center;
    margin: 0 auto 0.5em;
    font-weight: 400;
    color: #fff;
  }

  section {
    text-align: center;
  }

  .card-wrapper {
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    margin: 2.5em auto;
  }

  p {
    font-size: 20px;
  }

  .card-wrapper h2 {
    text-transform: uppercase;
    font-size: 1em;
    margin-top: 1em;
    font-weight: 300;
  }

  .news {
    margin: auto;
    margin-top: 3em;
  }

  /* .corona-map {
    margin-top: 3em;
    border: 1px solid #ccc;
  }

  .corona-map img {
    width: 100%;
  }
 */
  .card-wrapper h3 {
    font-size: 2.5em;
  }

  h4 {
    font-weight: 300;
  }

  .doctors {
    margin-top: 4em;
    margin-bottom: 6em;
  }

  .btn-contact {
    background: #000;
    border: 1px solid #000;
    background-image: var(--stripe);
    color: #fff;
    transition: 0.3s ease-in-out;
  }

  .btn-contact:hover {
    background: transparent;
    border: 1px solid #f1ecec;
    background-image: var(--stripe);
    color: #000;
    transition: 0.3s ease-in-out;
    box-shadow: 5px 5px 5px #b3b0b0;
  }

  .news {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
  }

  .deaths-log {
    transition: 0.3s ease-in-out;
  }

  .deaths-log:hover {
    transform: scale(1.05);
    transition: 0.3s ease-in-out;
  }

  .cards {
    width: 50%;
    height: 350px;
    margin: 1em;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin-top: 1.5em;
  }

  .cards img {
    width: 100%;
    height: 250px;
    object-fit: cover;
  }

  .date {
    height: 100px;
    margin-top: -9px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    max-width: 100%;
    background: #000;
    color: #fff;
    padding: 0.5em 0;
  }

  .date p {
    margin: 0;
  }

  .home {
    background: #2e519d;
    background-image: var(--stripe);
    color: #fff;
    padding: 1em;
    border-radius: 15px;
    margin: auto;
  }

  .donate {
    width: 100%;
    margin: auto;
  }

  .donate img {
    margin-top: 2em;
    width: 100%;
  }

  article img {
    max-width: 800px;
  }

  .gif img {
    margin-top: 3rem;
    margin-bottom: 3rem;
  }

  @media (max-width: 1440px) {
    h1 {
      font-size: 5em;
    }
    .main-title-hero h3 {
      font-size: 1.5em;
    }

    h2 {
      font-size: 2em;
    }
  }

  @media (max-width: 1024px) {
    p {
      font-size: 18px;
    }
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 4em;
    }
    .gif img {
      max-width: 100%;
    }
  }

  @media (max-width: 420px) {
    section {
      padding-top: 1em;
    }

    .main-bg-hero {
      height: 70vh;
    }

    .news {
      flex-direction: column;
    }

    .card-wrapper h3 {
      font-size: 2em;
    }

    .cards {
      width: 100%;
      height: auto;
    }

    .main-title-hero h3 {
      font-size: 1.2em;
    }

    .card-wrapper {
      flex-direction: column;
    }

    h1 {
      font-size: 3.5em;
    }

    h2 {
      font-size: 1.5em;
    }
  }

  @media (max-width: 320px) {
    h1 {
      font-size: 3em;
    }
    .cards img {
      max-height: 350px;
    }
  }
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Kezdőlap</title>
  <meta
    property="og:title"
    content="koronavírus-betegséggel kapcsolatos infomációk balassagyarmat és
    térsége számára." />
  <meta property="og:image" content="https://bgykaranten.hu/corona.jpg" />
  <meta property="og:url" content="https://bgykaranten.hu/" />
  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js">

  </script>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>KARANTÉN BGYARMAT</h1>
    <h3>
      koronavírussal (COVID-19) kapcsolatos tájékoztató oldal (nem csak)
      balassagyarmatiak számára
    </h3>
  </div>
</div>

<section>
  <div class="back doctors">
    <a href="/doctors" class="btn-contact">Háziorvosok elérhetőségei</a>
  </div>
  <hr />
  {#if isBlogs}
    <h2 class="first-h2">legfrissebb cikkeink</h2>
    <div class="news">
      <div class="cards">
        <a rel="prefetch" href="./blog/{posts[0].slug}">
          <img alt={posts[0].title} use:lazy={{ src: posts[0].thumbnail }} />
          <div class="date">
            <h3>{posts[0].title}</h3>
            <p>Közzétéve: {moment(posts[0].date).format('ll')}</p>
          </div>
        </a>
      </div>

      <div class="cards">
        <a rel="prefetch" href="./blog/{posts[1].slug}">
          <img alt={posts[1].title} use:lazy={{ src: posts[1].thumbnail }} />
          <div class="date">
            <h3>{posts[1].title}</h3>
            <p>Közzétéve: {moment(posts[1].date).format('ll')}</p>
          </div>
        </a>
      </div>
    </div>
    <div class="news">
      <a href="/blog" class="btn-contact">További cikkek, hírek</a>
    </div>
  {/if}
  <hr />
  <h2 class="first-h2">fertőzés helyzet magyarországon</h2>
  <h3>Utolsó frissítés dátuma: {moment(lastUpdateHun).format('lll')}</h3>
  <div class="card-wrapper">
    <Card>
      <div slot="name">
        <h2>Összes fertőzöttek</h2>
        <h3>{infectedHun}</h3>
      </div>
    </Card>
    <Card>
      <div slot="name">
        <h2>Gyógyult</h2>
        <h3>{recoveredHun}</h3>
      </div>
    </Card>
    <a
      class="deaths-log"
      href="https://koronavirus.gov.hu/elhunytak"
      title="Részletes adatok koronavirus.go.hu">
      <Card>
        <div slot="name">
          <h2>Elhunytak</h2>
          <h3>{deceasedHun}</h3>
        </div>
      </Card>
    </a>
    <Card>
      <div slot="name">
        <h2>Karanténban</h2>
        <h3>{quarantinedHun}</h3>
      </div>
    </Card>
    <Card>
      <div slot="name">
        <h2>Mintavétel</h2>
        <h3>{testedHun}</h3>
      </div>
    </Card>
  </div>
  <h4>
    Forrás:
    <a href="https://systems.jhu.edu/" target="_blank" rel="noreferrer">
      Johns Hopkins CSSE
    </a>
    <a href="https:/koronavirus.gov.hu" target="_blank" rel="noreferrer">
      ,koronavirus.gov.hu
    </a>
  </h4>

<!--   <div class="corona-map">
    <img
      use:lazy={{ src: 'https://koronavirus.gov.hu/sites/default/files/megye0124.png' }}
      alt="megyénkénti koronavírus statisztika" />
  </div> -->

  <hr />
  <h2 class="first-h2">fertőzés helyzet világszerte</h2>
  <h3>Utolsó frissítés dátuma: {moment(lastUpdateGlobal).format('lll')}</h3>
  <div class="card-wrapper">
    <Card>
      <img
        slot="logo"
        alt="corona logo"
        use:lazy={{ src: '.././img/corona-logo5.jpg' }} />
      <div slot="name">
        <h2>Fertőzöttek száma</h2>
        <h3>{confirmedGlobal}</h3>
      </div>
    </Card>
    <Card>
      <img
        slot="logo"
        alt="corona logo"
        use:lazy={{ src: '.././img/corona-logo5.jpg' }} />
      <div slot="name">
        <h2>Gyógyult</h2>
        <h3>{recoveredGlobal}</h3>
      </div>
    </Card>
    <Card>
      <img
        slot="logo"
        alt="corona logo"
        use:lazy={{ src: '.././img/corona-logo5.jpg' }} />
      <div slot="name">
        <h2>Elhunytak</h2>
        <h3>{deathsGlobal}</h3>
      </div>
    </Card>
  </div>
  <a href="https://systems.jhu.edu/" target="_blank" rel="noreferrer">
    <h4>Forrás: Johns Hopkins CSSE</h4>
  </a>
  <hr />
  <article class="gif">
    <h2 class="first-h2">Maradj otthon!</h2>
    <img
      alt="szigorítások május 22-ig tájékoztató"
      use:lazy={{ src: '.././img/covid_0508.jpg' }} />

    <h2 class="home">
      Nem csak jogaid, kötelességeid is vannak. Nem csak magadért, a
      családodért, hanem az egész társadalomért felelőséggel tartozol!
    </h2>
  </article>
  <!-- <hr /> -->
  <div class="donate">
    <h2 class="first-h2">Segíts hogy segíthessünk!</h2>
    <img
      alt="adomány számlaszám"
      use:lazy={{ src: '.././img/donation2.jpg' }} />
  </div>
</section>
