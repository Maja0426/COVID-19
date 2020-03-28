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
    margin: 3em 0;
    /* padding: 10px;
    font-size: 18px; */
  }

  h2 {
    font-size: 60px;
    text-align: center;
  }

  p,
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

    .btn-contact {
      background-image: var(--stripe);
      border-radius: 5px;
    }
  }

  @media (max-width: 420px) {
    li a {
      font-size: 14px;
    }
  }

  /* @media (max-width: 340px) {
    li a {
      font-size: 14px;
    }
  } */
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Háziorvosi ügyeletek</title>
</svelte:head>

<section>
  <div class="header-bg" />
  <h2>HÁZIORVOSI TELEFONOS ÜGYELET</h2>
  <p>
    Az EMMI miniszteri utasítása alapján a magas fertőzéses kockázat miatt
    megtiltották a felnőtt háziorvosoknak, hogy személyesen fogadjanak a
    rendelőben betegeket. Így városunkban is felnőtt betegfogadó rendelések
    megszűntek, csak telefonos rendelés, illetve receptfelírás történik.
  </p>
  <h3>
    Mobilkészülékről böngészve a telefonszámokra kattintva az adott hívás
    kezdeményezető!
  </h3>

  <ul>
    <li class=" bg-gearbox ">
      Dr. Csordás Ildikó (helyettesíti: Dr. Kenéz Katalin)
    </li>
    <li>
      <a href="tel:+3635300426" class="btn-contact">
        recept felírás (35)300-426
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36308644373">
        koronavírus tünet (30)864-4373
      </a>
    </li>
  </ul>
  <ul>

    <ul>
      <li class=" bg-gearbox ">
        Dr. Spruch Rezső (2020.04.01-ig helyettesíti Dr. Tassi Gábor)
      </li>
      <li>
        <a href="tel:+3680620011" class="btn-contact">
          recept felírás (80)620-011
        </a>
      </li>
      <li>
        <a class="btn-contact" href="tel:+36301451389">
          koronavírus tünet (30)145-1389
        </a>
      </li>
    </ul>

    <li class=" bg-gearbox ">
      Dr. Kubassek Péter (2020.03.29-ig helyettesíti: Dr. Kenéz Katalin))
    </li>
    <li>
      <a href="tel:+3635300053" class="btn-contact">
        recept felírás (35)300-053
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36204250197">
        koronavírus tünet (20)425-0197
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Váradi Erzsébet</li>
    <li>
      <a href="tel:+3635301815" class="btn-contact">
        recept felírás (35)301-815
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36308955342">
        koronavírus tünet (30)895-5342
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Tassi Gábor</li>
    <li>
      <a href="tel:+3635300500" class="btn-contact">
        recept felírás (35)300-500
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36301451389">
        koronavírus tünet (30)145-1389
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Faragó Gyöngyi</li>
    <li>
      <a href="tel:+3635315752" class="btn-contact">
        recept felírás (35)315-752
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+3635315752">
        koronavírus tünet (35)315-752
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">
      Dr. Varga Ágnes (helyettesíti: Dr. Tassi Gábor)
    </li>
    <li>
      <a href="tel:+3635300500" class="btn-contact">
        recept felírás (35)300-500
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36301451389">
        koronavírus tünet (30)145-1389
      </a>
    </li>
  </ul>

  <h3>
    A vonalak leterheltsége miatt kérjük türelmüket és köszönjük megértésüket!
  </h3>
</section>
