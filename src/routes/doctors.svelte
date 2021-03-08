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

  .btn-contact {
    background: #fff;
    background-image: var(--stripe);
    border: none;
    box-shadow: 5px 5px 5px #b3b0b0;
    transition: 0.3s ease-in-out;
    border: 1px solid transparent;
  }

  .btn-contact:hover {
    background: transparent;
    color: #000;
    box-shadow: none;
    transition: 0.3s ease-in-out;
    border: 1px solid #f1ecec;
  }

  li {
    text-align: center;
    margin: 3em 0;
    padding: 10px 0;
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

  .important-text {
    text-transform: uppercase;
    margin-top: 4em;
    font-size: 2rem;
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
      border-radius: 50px;
      box-shadow: 5px 5px 5px #b3b0b0;
      font-weight: bold;
      max-width: 300px;
    }

    li {
      margin-bottom: 1em;
    }
  }

  @media (max-width: 420px) {
    li a {
      font-size: 14px;
    }

    .important-text {
      font-size: 1.3rem;
      line-height: 1.5;
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
      Dr. Csordás Ildikó
    </li>
    <li>
      <a href="tel:+3635300426" class="btn-contact">
        Vezetékes hívószám: (35)300-426
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36308644373">
        koronavírus tünet (30)864-4373
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Spruch Rezső</li>
    <li>
      <a href="tel:+3635310493" class="btn-contact">
        Vezetékes hívószám: (35)310-493
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36204957746">
        koronavírus tünet (20)495-7746
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Kubassek Péter</li>
    <li>
      <a href="tel:+3635300053" class="btn-contact">
        Vezetékes hívószám: (35)300-053
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
        Vezetékes hívószám: (35)301-815
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
        Vezetékes hívószám: (35)300-500
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36301451389">
        Mobil: (30)145-1389
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">Dr. Faragó Gyöngyi</li>
    <li>
      <a href="tel:+3635315752" class="btn-contact">
        Vezetékes hívószám: (35)315-752
      </a>
    </li>
  </ul>

  <ul>
    <li class=" bg-gearbox ">
      Dr. Varga Ágnes
    </li>
    <li>
      <a href="tel:+3635300500" class="btn-contact">
        Vezetékes hívószám: (35)300-500
      </a>
    </li>
    <li>
      <a class="btn-contact" href="tel:+36301451389">
        Mobil: (30)145-1389
      </a>
    </li>
  </ul>

  <h3 class="important-text">
    A vonalak leterheltsége miatt kérjük türelmüket és köszönjük megértésüket!
  </h3>
</section>
