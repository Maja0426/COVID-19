<style>
  .bg-gearbox {
    background-color: var(--main-color);
    background-image: var(--stripe);
    color: #fff;
    font-size: 28px;
    padding: 10px;
    margin-top: 40px;
    max-width: 900px;
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

  h2 {
    font-size: 60px;
    text-align: center;
  }

  h3 {
    text-align: center;
    margin-top: 1em;
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
  <title>Koronavírus Balassagyarmat | Fogorvosi ügyeletek</title>
</svelte:head>

<section>
  <div class="header-bg" />
  <h2>FOGORVOSI ÜGYELET</h2>
  <h3>
    A koronavírus miatt elrendelt veszélyhelyzet ideje alatt a fogorvosi
    alapellátók csak sürgősségi beavatkozásokat végezhetnek. Városunk ügyeleti
    rendje:
  </h3>

  <ul>
    <li class=" bg-gearbox ">1. körzet Rendelőintézet (Szontagh u.)</li>
    <li>Hétfő: 13:00 – 16:00</li>
    <li>Kedd: 08:30 – 11:30</li>
    <li>Szerda: 10:00 – 13:00</li>
    <li>Csütörtök: 08:30 – 11:30</li>
    <li>Péntek: Betegellátás a 2. körzet rendelőjében</li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">2. körzet Ipolyjáró utca</li>
    <li>Hétfő: 14:00 – 17:00</li>
    <li>Kedd: Betegellátás az 1., 3. és 5. körzetek rendelőiben</li>
    <li>Szerda: 14:00 – 17:00</li>
    <li>Csütörtök: 08:00 – 11:00</li>
    <li>Péntek: 08:00 – 11:00</li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">3. körzet Rendelőintézet (Szontagh u.)</li>
    <li>Hétfő: 13:00 – 16:00</li>
    <li>Kedd: 08:30 – 11:30</li>
    <li>Szerda: 10:00 – 13:00</li>
    <li>Csütörtök: 08:30 – 11:30</li>
    <li>Péntek:Betegellátás a 2. körzet rendelőjében</li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">4. körzet Jókai u.</li>
    <li>
      Helyettesített körzet. A betegeket rendelési időben az 1., 3. és 5. körzet
      orvosai látják el.
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">5. körzet Rendelőintézet (Szontagh u.)</li>
    <li>Hétfő: 13:00 – 16:00</li>
    <li>Kedd: 08:30 – 11:30</li>
    <li>Szerda: 10:00 – 13:00</li>
    <li>Csütörtök: 08:30 – 11:30</li>
    <li>Péntek: Betegellátás a 2. körzet rendelőjében</li>
  </ul>
</section>
