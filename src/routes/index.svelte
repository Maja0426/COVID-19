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

  const covidHunUrl = "https://covid19.mathdro.id/api/countries/hu";
  const covidGlobalUrl = "https://covid19.mathdro.id/api/";

  let confirmedHun;
  let recoveredHun;
  let deathsHun;
  let confirmedGlobal;
  let recoveredGlobal;
  let deathsGlobal;
  let lastUpdateGlobal, lastUpdateHun;

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
      }, 200);
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
      const responseGlobal = await axios.get(covidGlobalUrl);
      confirmedHun = responseHun.data.confirmed.value;
      recoveredHun = responseHun.data.recovered.value;
      deathsHun = responseHun.data.deaths.value;
      lastUpdateHun = responseHun.data.lastUpdate;
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

  #about {
    padding-bottom: 2em;
  }

  #about h3 {
    display: flex;
    justify-content: center;
  }

  #about a:hover {
    text-decoration: underline;
  }

  p {
    font-size: 20px;
  }

  .main-title-hero h3 {
    color: #fff;
    text-align: center;
    font-size: 1.7em;
    font-weight: 300;
    text-transform: uppercase;
  }

  .card-wrapper h2 {
    text-transform: uppercase;
    font-size: 1em;
    margin-top: 1em;
    font-weight: 300;
  }

  .card-wrapper h3 {
    font-size: 3em;
  }

  h4 {
    font-weight: 300;
  }

  .main-bg-hero {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: url(".././img/covid-wallpaper.png") no-repeat 10% center/cover;
    width: 100%;
    height: 60vh;
  }

  .main-title-hero {
    display: flex;
    flex-direction: column;
    padding: 0 5%;
    opacity: 1;
    margin-top: 100px;
  }

  .home {
    background: #ff0000;
    color: #000;
    padding: 1em;
    border-radius: 15px;
  }

  .cards {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin-top: 1.5em;
  }

  .date {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    background: #000;
    color: #fff;
  }

  .date p,
  .date h2 {
    margin: 0;
  }

  .cards img {
    width: 100%;
    height: auto;
    max-height: 500px;
  }

  @media (max-width: 1366px) {
    h1 {
      font-size: 5em;
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
    .main-bg-hero {
      height: 70vh;
    }

    .news {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    .main-title-hero h3 {
      font-size: 1.2em;
    }

    .card-wrapper {
      flex-direction: column;
    }

    section#about {
      margin-bottom: -4em;
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
  <title>Balassagyarmat Koronavírus | Főoldal</title>
  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js">

  </script>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>
      COVID-19
      <br />
      - INFO -
    </h1>
    <h3>
      koronavírussal (COVID-19) kapcsolatos tájékoztató oldal (nem csak)
      balasssagyarmatiak számára
    </h3>
  </div>
</div>

<section class="news">
  <h2 class="first-h2">legfrissebb cikkünk</h2>
  <div class="cards">

    <a rel="prefetch" href="./blog/{posts[0].slug}">
      <img alt="corona logo" src={posts[0].thumbnail} />
      <div class="date">
        <h2>{posts[0].title}</h2>
        <p>Közzétéve: {moment(posts[0].date).format('ll')}</p>
      </div>
    </a>
  </div>
</section>

<section class="about" id="about">
  <h2 class="first-h2">fertőzés helyzet magyarországon</h2>
  <h3>Utolsó frissítés dátuma: {moment(lastUpdateHun).format('lll')}</h3>
  <div class="card-wrapper">
    <Card>
      <h2 slot="name">Összes fertőzöttek</h2>
      <h3 slot="number">{confirmedHun}</h3>
    </Card>
    <Card>
      <h2 slot="name">Gyógyult</h2>
      <h3 slot="number">{recoveredHun}</h3>
    </Card>
    <Card>
      <h2 slot="name">Elhunytak</h2>
      <h3 slot="number">{deathsHun}</h3>
    </Card>
    <!-- <Card>
      <h2 slot="name">Jelenleg fertőzöttek</h2>
      <h3 slot="number">{confirmedHun - recoveredHun - deathsHun}</h3>
    </Card> -->
  </div>
  <a href="https://systems.jhu.edu/" target="_blank" rel="noreferrer">
    <h4>Forrás: Johns Hopkins CSSE</h4>
  </a>

  <hr />
  <h2 class="first-h2">fertőzés helyzet világszerte</h2>
  <h3>Utolsó frissítés dátuma: {moment(lastUpdateGlobal).format('lll')}</h3>
  <div class="card-wrapper">
    <Card>
      <h2 slot="name">Fertőzöttek száma</h2>
      <h3 slot="number">{confirmedGlobal}</h3>
    </Card>
    <Card>
      <h2 slot="name">Gyógyult</h2>
      <h3 slot="number">{recoveredGlobal}</h3>
    </Card>
    <Card>
      <h2 slot="name">Elhunytak</h2>
      <h3 slot="number">{deathsGlobal}</h3>
    </Card>
  </div>
  <a href="https://systems.jhu.edu/" target="_blank" rel="noreferrer">
    <h4>Forrás: Johns Hopkins CSSE</h4>
  </a>
</section>

<section>
  <article class="gif">
    <h2 class="first-h2">Maradj otthon!</h2>
    <img
      alt="miért maradj otthon animáció"
      use:lazy={{ src: '.././img/covid-gif.gif' }} />
    <p>
      Most a legfontosabb, hogy a vírus terjedését lelassítsuk. Ezért nagyon
      fontos, hogy aki teheti, maradjon otthon. Ha hirtelen sokan betegednek
      meg, az túlterheli az egészségügyi ellátó rendszert, és nem tudja
      kiszolgálni a nagy tömegben jelentkező betegeket. Ez történt
      olaszországban is, ezt szemlélteti a fenti animáción a kiugró görbe. Ha
      viszont nem tömegek, hanem viszonylag egyenletes ütemben kisebb létszámú
      csoportok lesznek betegek (ami elkerülhetetlen) akkor a "kritikus" tömeg
      mennyisége kezelhető szinten marad, azaz az animáción a szaggatott vonal
      alatt, ami a rendszer kapacitását szimbolizálja. Fontos hogy ne essünk
      pánikba, de gondolkozzunk és viselkedjünk felelős állampolgárok módján.
    </p>

    <h2 class="home">
      Nem csak jogaid, kötelességeid is vannak. Nem csak magadért, a
      családodért, hanem az egész társadalomért felelőséggel tartozol!
    </h2>
  </article>
</section>
