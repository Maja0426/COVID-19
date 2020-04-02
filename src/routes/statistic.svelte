<script>
  import Charts from "../components/Charts.svelte";
  /* import axios from "axios";
  import { onMount } from "svelte"; */

  /* const covidHunUrl =
    "https://api.apify.com/v2/datasets/Gm6qjTgGqxkEZTkuJ/items?format=json&clean=1";

  let deceasedHun, recoveredHun, quarantinedHun, testedHun;
  let infectedHun = [];

  onMount(async function getData() {
    try {
      const responseHun = await axios.get(covidHunUrl);
      infectedHun = infectedHun.data.infected;
      deceasedHun = responseHun.data.deceased;
      recoveredHun = responseHun.data.recovered;
      quarantinedHun = responseHun.data.quarantined;
      testedHun = responseHun.data.tested;
    } catch (error) {
      console.log(error);
    }
  }); */
</script>

<style>
  h1 {
    font-size: 6em;
    text-align: center;
    margin: 0 auto 0.5em;
    font-weight: 400;
    color: #fff;
  }

  .main-bg-hero {
    background: url(".././img/chart.png") no-repeat 10% center/cover;
  }

  h3 {
    font-size: 1.5em;
    text-transform: uppercase;
  }

  p {
    font-size: 20px;
    text-align: center;
  }

  .main-title-hero h3 {
    color: #fff;
    text-align: center;
    font-size: 1.7em;
    font-weight: 300;
  }

  h2 {
    text-align: center;
    font-size: 2.5em;
  }

  article {
    margin-bottom: 3em;
  }

  p {
    font-size: 14px;
  }

  /*  iframe {
    display: flex;
    max-width: 100%;
    justify-content: center;
    margin: auto;
  } */

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

  @media (max-width: 768px) {
    .main-bg-hero {
      position: relative;
      left: 0;
      top: 0;
    }

    h1 {
      font-size: 4em;
    }

    h2 {
      font-size: 20px;
    }
  }

  @media (max-width: 420px) {
    .main-bg-hero {
      height: 70vh;
      /* transform: skewY(0deg); */
    }

    .main-title-hero h3 {
      font-size: 1.2em;
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
  }
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Statisztikai adatok</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Statisztikai adatok</h1>
    <h3>A magyarországi statisztikai adatok grafikonon ábrázolva</h3>
  </div>
</div>
<section>
  <article>
    <h2>COVID-19 igazolt fertőzöttek számának alakulása magyarországon*</h2>
    <Charts
      comment=" (*Forrás: koronavirus.gov.hu, 03. havi állapot)"
      coordinateY={[0, 30, 60, 90, 120, 150, 180, 210, 240, 270, 300, 330, 360, 390, 420, 450, 480, 510]}
      coordinateX={[15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31]}
      perc={[32, 39, 50, 58, 73, 85, 103, 131, 167, 187, 226, 261, 300, 343, 408, 447, 492]} />

    <Charts
      comment=" (*Forrás: koronavirus.gov.hu, 04. havi állapot)"
      coordinateY={[0, 40, 80, 120, 160, 200, 240, 280, 320, 360, 400, 440, 480, 520, 560, 600, 640, 680]}
      coordinateX={[01, 02]}
      perc={[525, 585]} />
    <p>x koordnáta: dátum, y koordináta: megbetegedések száma</p>
  </article>
  <article>
    <h2>COVID-19 vírusfertőzés miatti halálesetek magyarországon*</h2>
    <Charts
      barColor="#222222"
      comment=" (*Forrás: koronavirus.gov.hu, 03. havi állapot)"
      coordinateY={[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30]}
      coordinateX={[15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31]}
      perc={[1, 1, 1, 1, 1, 4, 4, 6, 8, 9, 10, 10, 10, 11, 13, 15, 16]} />

    <Charts
      barColor="#222222"
      comment=" (*Forrás: koronavirus.gov.hu, 04. havi állapot)"
      coordinateY={[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30]}
      coordinateX={[01, 02]}
      perc={[20, 21]} />
    <p>x koordnáta: dátum, y koordináta: halálesetek száma</p>
  </article>
</section>

<!-- <iframe
  title="covid-19 statistic"
  width="95%"
  height="800px"
  src="https://haarp.hu/"
  frameborder="1" />
 -->
