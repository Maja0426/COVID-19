<style>
  section {
    display: flex;
    flex-direction: column;
    padding: 8em 5% 0;
  }

  h3,
  .link {
    text-align: center;
  }

  p {
    font-size: 18px;
  }

  figure {
    text-align: center;
  }

  li {
    text-align: center;
    padding: 10px;
    font-size: 18px;
    font-weight: bold;
  }

  h1 {
    font-size: 60px;
    text-align: center;
  }

  h2 {
    background-color: var(--main-color);
    background-image: var(--stripe);
    color: #fff;
    font-size: 28px;
    padding: 10px;
    margin-top: 40px;
    max-width: 1100px;
    margin: 50px auto 20px;
    text-align: center;
  }

  ul {
    list-style: none;
    padding-inline-start: 0;
  }

  figure img {
    width: 200px;
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 28px;
    }

    h2 {
      font-size: 22px;
    }

    p {
      font-size: 16px;
    }
  }
</style>

<svelte:head>
  <title>Smart-Bee Web | Cookies</title>
</svelte:head>

<section>
  <div class="header-bg" />
  <h1>Sütik (cookie-k) kezelése</h1>
  <br />
  <h2>
    Oldalunk sütiket (cookies) használ az oldal működtetése, használatának
    megkönnyítése illetve az oldalon végzett tevékenység nyomon követése
    érdekében.
  </h2>
  <figure class="text-center">
    <img src="./cookie.png" alt="Sütik" />
  </figure>
  <p>
    A süti (cookie) egy rövid szöveg, amelyet a felkeresett webhely küld el
    böngészőjébe. Segítségével a webhely megjegyzi a látogatásával kapcsolatos
    információkat, például az Ön által használt nyelvet és egyéb beállításokat.
    Ezáltal gördülékenyebbé válhat a következő látogatás, és könnyebb lesz a
    webhely használata. A sütik fontos szerepet játszanak. Nélkülük az internet
    használata sokkal nehézkesebb lenne.
  </p>
  <div>
    <ul>
      <li>
        <p>
          A sütiknek az engedélyezése nem feltétlenül szükséges a webhely
          működéséhez, de javítja a böngészés élményét és teljesítményét.
        </p>
      </li>
      <li>
        <p>
          Ön törölheti vagy letilthatja ezeket a sütiket, de ebben az esetben
          előfordulhat, hogy a webhely bizonyos funkciói nem működnek
          rendeltetésszerűen.
        </p>
      </li>
      <li>
        <p>
          A sütik által tárolt információkat nem használjuk fel az Ön
          személyazonosságának megállapítására, és a mintaadatok teljes
          mértékben az ellenőrzésünk alatt állnak.
        </p>
      </li>
    </ul>
  </div>
  <h2>Milyen sütiket használunk és mire?</h2>
  <div>
    <div>
      <div>
        <p>
          Információ gyűjtése, hogy milyen módon használja weboldalunkat (annak
          felmérésével, hogy weboldalunk melyik részeit látogatja vagy használja
          leginkább), így tudunk biztosítani még jobb felhasználói élményt, ha
          újra meglátogatja oldalunkat.
        </p>
      </div>
    </div>
    <div>
      <div>
        <p>
          A felhasználó által az oldalon végzett tevékenységének nyomon
          követésére azért, hogy az Önt érdeklő vagy Önnek fontos ajánlatokról
          üzenetet juttathassunk el az Ön számára.
        </p>
      </div>
    </div>
  </div>
  <h2>Az általunk használt sütik típusai</h2>
  <div>
    <div>
      <div>
        <h3>Alapműködést biztosító sütik</h3>
        <p>
          Ezen sütik biztosítják a weboldal megfelelő működését, megkönnyítik
          annak használatát, és látogatóink azonosítása nélkül gyűjtenek
          információt a használatáról.
        </p>
        <p>
          Ilyen a sütikezelés elfogadásának státusza, az ikonkészletet biztosító
          fontawesome sütije és a részleges funkcionalitású Google Analytics
          kód.
        </p>
        <h3>Statisztikai célú sütik</h3>
        <p>
          A felhasználói élmény javítása céljából olyan sütiket is használunk,
          mely lehetővé teszi számunkra hogy információt szerezzünk látogatóink
          weboldalunkkal kapcsolatos használatának módjáról. Ezek a sütik nem
          tudják a felhasználót beazonosítani. Ezen sütik olyan információkat
          gyűjtenek mint például: Ön melyik oldalt nézte meg, mennyi időt
          töltött el az adott oldalon, melyik lapról hagyta el oldalunkat.
        </p>
        <p>
          Ilyen teljesítményt biztosító sütik a Google Analytics sütijei is. A
          Google Analitics sütikkel kapcsolatos részletes tájékoztatásért
          <a
            href="https://developers.google.com/analytics/devguides/collection/analyticsjs/cookie-usage"
            target="_blank">
            kattintson ide.
          </a>
        </p>
        <h3>Célzó- és hirdetési sütik</h3>
        <p>
          Ezeknek a sütiknek az a célja, hogy az Önt leginkább vagy az Ön
          számára leginkább jelentőséggel bíró hirdetések jelenjenek meg az
          oldalakon. Ezek a sütik nem tudják a felhasználót beazonosítani. Ezen
          sütik olyan információkat gyűjtenek mint például: Ön melyik oldalt
          nézte meg, mennyi időt töltött el az adott oldalon, melyik lapról
          hagyta el oldalunkat.
        </p>
      </div>
    </div>
  </div>
  <h2>Weboldalunkon a következő szolgáltatók sütijeit használjuk:</h2>
  <div>
    <div>
      <div>
        <h3>Google Adwords</h3>
        <p class="link">
          Részletes tájékoztató az alábbi linken:
          <a href="https://policies.google.com/privacy?hl=hu" target="_blank">
            https://policies.google.com/privacy?hl=hu
          </a>
        </p>
      </div>
    </div>
  </div>
  <h2>Hogyan lehet a sütiket ellenőrizni és kikapcsolni:</h2>
  <div>
    <div>
      <div>
        <p>
          Minden modern böngésző kötelező eleme annak engedélyezése, hogy a
          felhasználó kézben tarthassa a sütik beállítását, azt
          megváltoztathassa. A böngészők általában véve automatikusan elfogadják
          a sütiket, azonban lehetőség van arra is, hogy ezt megváltoztassuk.
          Így a böngésző meg tudja akadályozni hogy a sütiket automatikusan
          elfogadja, és felajánlja a lehetőséget, hogy a felhasználó
          engedélyezi-e a sütiket.
        </p>
      </div>
    </div>
  </div>
</section>
