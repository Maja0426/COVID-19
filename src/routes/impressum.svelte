<style>
  .bg-gearbox {
    background-color: var(--main-color);
    background-image: var(--stripe);
    color: #fff;
    font-size: 28px;
    padding: 10px;
    margin-top: 40px;
    max-width: 500px;
    margin: 50px auto 20px;
  }

  section {
    padding-top: 8em;
  }

  li {
    text-align: center;
    padding: 10px;
    font-size: 18px;
  }

  b {
    display: block;
  }

  a {
    text-decoration: underline;
  }

  a:hover {
    color: var(--main-color);
  }

  h2 {
    font-size: 60px;
    text-align: center;
  }

  ul {
    list-style: none;
    padding-inline-start: 0;
  }

  @media (max-width: 768px) {
    section {
      padding-top: 100px;
      margin: 0 2% 3%;
    }

    h2 {
      font-size: 40px;
    }
  }
</style>

<svelte:head>
  <title>Smart-Bee Web | Impresszum</title>
</svelte:head>

<section>
  <div class="header-bg" />
  <h2>Impresszum</h2>
  <ul>
    <li class=" bg-gearbox ">Tárhelyszolgáltató</li>
    <li>
      <b>Cégnév:Netlify Inc.</b>
      <img src="./logomark.png" style="width: 50px;" alt="Netlify logo" />
    </li>

    <li>
      <b>Székhely:</b>
      610 22nd St #315, San Francisco
    </li>
    <li>
      <b>Levelezési cím:</b>
      610 22nd St #315, San Francisco
    </li>
    <li>
      <b>Email:</b>
      <a href="mailto:support@netlify.com">support@netlify.com</a>
    </li>
    <li class="bg-gearbox">Weboldal Üzemeltetője</li>
    <li>
      <b>Majoros Tamás e.v.</b>
    </li>
    <li>
      <b>Székhely / levelezési cím:</b>
      2660 Balassagyarmat, Patvarci utca 18.
    </li>
    <li>
      <b>Nyilvántartásba bejegyző hatóság:</b>
      Belügyminisztérium Nyilvántartások Vezetéséért Felelős Helyettes
      Államtitkár Okmányfelügyeleti Főosztály
    </li>
    <li>
      <b>Nyilvántartási szám:</b>
      52682997
    </li>
    <li>
      <b>Adószám:</b>
      69089516-1-51
    </li>
    <li>
      <b>Telefonszám:</b>
      <a href="tel:+36705301130">+36(70)530-1130</a>
    </li>
    <li>
      <b>E-mail cím:</b>
      <a href="mailto:develop.tmsmajoros@gmail.com">
        develop.tmsmajoros@gmail.com
      </a>
    </li>
    <li>
      <b>Iparkamara:</b>
      Nógrád Megyei Kereskedelmi és Iparkamara
    </li>
  </ul>
</section>
