<script>
  import { onMount, onDestroy } from "svelte";
  import Modal from "../components/Modal.svelte";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  const loaded = new Map();
  let visible = false;
  let open = false;

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

  function openModal(name) {
    open = name;
  }

  function cancel() {
    open = false;
  }
</script>

<style>
  section {
    display: flex;
    justify-content: space-around;
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
    background: url("../img/food2.jpg") no-repeat center/cover;
  }

  .first-h2 {
    margin-top: 2em;
  }

  .cards {
    width: 45%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    background: #fff;
    box-shadow: 3px 3px 5px #222;
    margin-bottom: 3em;
  }

  .row-wrapper {
    display: flex;
  }

  .title {
    display: flex;
    justify-content: center;
    align-items: center;
    text-transform: uppercase;
    text-align: center;
    padding: 1em;
  }

  .title h2 {
    font-weight: 300;
    font-size: 30px;
  }

  .body {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-width: 200px;
    background: #fff;
    color: #222;
  }

  .image {
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fff;
    margin: 1em;
    padding: 0;
  }

  .image:hover {
    cursor: pointer;
    filter: grayscale(1);
  }

  .image,
  .body {
    display: flex;
    flex-direction: column;
  }

  img {
    min-width: 100px;
    width: 100%;
    object-fit: cover;
    border-radius: 5px;
  }

  h3,
  h1 {
    text-align: center;
    padding: 0.5em;
  }

  .btn-contact {
    background: #c31f09;
    background-image: var(--stripe);
    color: #fff;
    border: 2px solid #c31f09;
    text-transform: uppercase;
    padding: 0.7em 2em;
    margin-top: 1em;
    border-radius: 50px;
    transition: 0.2s ease-in-out;
  }

  .btn-contact:hover {
    background: #fff;
    background-image: var(--stripe);
    color: #000;
    border: 2px solid #000;
    transition: 0.2s ease-in-out;
  }

  .modal-btn {
    margin-bottom: 1em;
    background: transparent;
    color: #000;
    margin-right: auto;
    margin-left: auto;
  }

  .modal-btn:hover {
    margin-bottom: 1em;
    background: #000;
    color: #fff;
  }

  p {
    margin: 1em;
    text-align: center;
  }

  ul {
    padding-top: 1em;
    list-style: none;
  }

  li {
    margin: auto;
  }

  @media (max-width: 1440px) {
    h1 {
      font-size: 5em;
    }
    .main-title-hero h3 {
      font-size: 1.5em;
    }
  }

  @media (max-width: 1024px) {
    .btn-contact {
      padding: 0.7em 1em;
    }

    .row-wrapper {
      flex-direction: column;
      width: 100%;
    }

    .cards {
      margin: 1em;
      padding: 0;
    }

    p {
      font-size: 14px;
    }
  }

  @media (max-width: 768px) {
    .btn-contact {
      padding: 0.7em;
    }

    .row-wrapper {
      flex-direction: column;
      width: 100%;
    }

    .cards {
      margin: 0.5em;
      padding: 0;
    }

    p {
      font-size: 14px;
    }
  }

  @media (max-width: 420px) {
    section {
      padding: 4em 1em;
    }

    .cards {
      width: 100%;
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
    section {
      padding: 4em 0.5em;
    }
    h1 {
      font-size: 3em;
    }
    .main-title-hero h3 {
      font-size: 1em;
    }
  }
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Étel Házhozszállítás</title>
  <meta property="og:image" content="https://bgykaranten-hu/img/food2.jpg" />
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>ÉTEL RENDELÉS</h1>
    <h3>
      Honnan, mikor, milyen kaját tudsz rendelni, milyen módon, egyéb infók
      rendeléssel, házhozszállítással kapcsolatban.
    </h3>
  </div>
</div>

<h2 class="first-h2">Bővebb információért kattints az étterem logójára!</h2>

<section>
  <div class="cards">
    <div class="col-wrapper">
      <div class="title">
        <h2>Art Cafe</h2>
      </div>
      <div class="row-wrapper">
        <div class="image" on:click={() => openModal('artcafe')}>
          <img
            alt="art cafe logo"
            use:lazy={{ src: '../shops/artcafelogo.jpeg' }} />
        </div>
        <div class="body">
          <a href="tel:+36306616126" class="btn-contact">+36(30)661-6126</a>
          <a href="tel:+36303301771" class="btn-contact">+36(3)033-01771</a>
          <p>
            HÉTFŐTŐL-CSÜTÖRTÖKIG :10:00-21:00
            <br />
            PÉNTEK-SZOMBAT: 10:00-22:00
            <br />
            VASÁRNAP : 10:00-21:00
          </p>
        </div>
      </div>
    </div>
  </div>

  <div class="cards">
    <div class="col-wrapper">
      <div class="title">
        <h2>Excalibur étterem</h2>
      </div>
      <div class="row-wrapper">
        <div class="image" on:click={() => openModal('excalibur')}>
          <img alt="dgs" use:lazy={{ src: '../img/noimage.jpg' }} />
        </div>
        <div class="body">
          <a href="tel:+36202943900" class="btn-contact">+36(20)294-3900</a>
          <p>(Fenti telefonszám info vonal, rendelést nem vesznek fel)</p>
          <p>
            HÉTFŐTŐL-PÉNTEKIG :11:00-13:30
            <br />
            SZOMBAT-VASÁRNAP: Zárva
            <br />
            Minimum rendelési összeg: 900 Ft
          </p>
        </div>
      </div>
    </div>
  </div>

</section>

<!--            MODAL            -->

{#if open === 'artcafe'}
  <Modal title="Információ" on:cancel={cancel}>
    <h3>
      Balassagyarmaton ingyenes a kiszállítas, a többi településre 3
      ételrendelés plusz útiköltseggel tudunk kiszállítani.
    </h3>
    <ul>
      <li>Patvarc : 500ft</li>
      <li>Szügy : 500ft</li>
      <li>Őrhalom : 800ft</li>
      <li>Hugyag : 1000ft</li>
      <li>Mohora: 1000ft</li>
      <li>Nyírjes : 400ft</li>
      <li>Gyárak : 400ft</li>
      <li>Ipolyszög : 500ft</li>
      <li>Ipolyvece : 1200ft</li>
      <li>Érsekvadkert: 1200ft</li>
      <li>Dejtár : 1000ft</li>
      <li>Szlovákgyarmat : 300ft</li>
    </ul>
    <h3>Fizetési lehetőség: a futárnál készpénzzel, illetve bankkártyával:</h3>
    <button class="modal-btn">
      <a
        href="https://www.telepocak.hu/menu-art-cafe"
        target="_blank"
        rel="noreferrer">
        telepocak
      </a>
    </button>
    <div slot="footer">
      <button on:click={cancel}>Bezár</button>
    </div>
  </Modal>
{:else if open === 'excalibur'}
  <Modal title="Információ" on:cancel={cancel}>
    <h3>Excalibur étterem 2660 Balassagyarmat Teleki 2.</h3>
    <p>Bővebb információk:</p>
    <button class="modal-btn">
      <a href="http://bgyebed.hu/" target="_blank" rel="noreferrer">
        bgyebed.hu
      </a>
    </button>
    <button class="modal-btn">
      <a href="http://bgypizza.hu/" target="_blank" rel="noreferrer">
        bgypizza.hu
      </a>
    </button>
    <div slot="footer">
      <button on:click={cancel}>Bezár</button>
    </div>
  </Modal>
{/if}
