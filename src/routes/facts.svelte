<style>
  h1 {
    font-size: 6em;
    text-align: center;
    margin: 0 auto 0.5em;
    font-weight: 400;
    color: #fff;
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

  .main-bg-hero {
    background: url("../img/corona-logo3.jpg") no-repeat center/cover;
  }

  .container {
    margin-top: 3em;
    display: flex;
    flex-direction: row;
    width: 100%;
  }

  .text-container {
    width: calc(100% - 200px);
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    padding: 0 2em;
  }

  .text-container h3 {
    font-size: 1.3em;
    text-transform: none;
  }

  .logo-container {
    /* background-color: #f7f8f8; */
    width: 200px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 5px;
  }

  .logo-container img {
    width: 140px;
    height: 140px;
    border-radius: 100%;
  }

  @media (max-width: 1366px) {
    h1 {
      font-size: 5em;
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
  }

  @media (max-width: 420px) {
    .container {
      flex-direction: column;
    }

    .container h3 {
      margin-top: 1em;
    }

    .text-container,
    .logo-container {
      width: 100%;
      align-items: center;
      justify-content: center;
      padding: 0;
    }

    .logo-container {
      background-color: inherit;
      height: 200px;
    }

    .main-title-hero h3 {
      font-size: 1.2em;
    }

    h1 {
      font-size: 3.5em;
    }
  }

  @media (max-width: 320px) {
    h1 {
      font-size: 3em;
    }
  }
</style>

<svelte:head>
  <title>Koronavírus Balassagyarmat | Tények-tévhitek</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Tények és tévhitek</h1>
    <h3>
      Tények és tévhitek a COVID-19 koronavírussal kapcsolatban, a WHO hivatalos
      álláspontja alapján.
    </h3>
  </div>
</div>

<section>

  <div class="container">
    <div class="logo-container">
      <img src="../img/who/52.png" alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        A COVID-19 vírus terjedhet forró és párás éghajlattal rendelkező
        területeken?
      </h3>
      <p>
        Az eddigi bizonyítékok alapján a COVID-19 vírus terjedhet MINDEN
        TERÜLETEN, ideértve a forró és párás időjárási területeket is. Az
        éghajlattól függetlenül fogadjon el védőintézkedéseket, ha a COVID-19-et
        jelentő térségben él vagy utazik. A COVID-19 elleni védekezés legjobb
        módja a keze gyakori tisztítása. Ezzel kiküszöböli a kezén lévő
        vírusokat, és elkerüli a fertőzést, amely akkor fordulhat elő, ha
        megérinti a szemét, a száját és az orrát.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mb-cold-snow.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>A hideg idő és a hó meg tudja ölni az új koronavírust?</h3>
      <p>
        Nincs ok azt hinni, hogy a hideg időjárás elpusztíthatja az új
        koronavírust vagy más betegségeket. Az emberi test normál hőmérséklete
        36,5 - 37 ° C körül marad, függetlenül a külső hőmérséklettől vagy az
        időjárástól. A leghatékonyabb módja annak, hogy megvédje magát az új
        koronavírus ellen, ha gyakran megtisztítja a kezét alkohol tartalmú
        kéztörlővel vagy szappannal és vízzel.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mb-hot-bath.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Forró fürdő használata megakadályozhatja az új koronavírus betegséget?
      </h3>
      <p>
        Forró fürdő használata nem akadályozza meg a COVID-19 elkapását. Normál
        testhőmérséklete 36,5 - 37 ° C körül marad, függetlenül a fürdő vagy a
        zuhany hőmérsékletétől. Valójában egy rendkívül forró vízzel történő
        fürdő használata káros lehet, mivel megéghet. A COVID-19 elleni
        védekezés legjobb módja a keze gyakran tisztítása. Ezzel kiküszöböli a
        kezén lévő vírusokat, és elkerülheti a heveny fertőzéseket, amikor
        megérinti a szemét, a száját és az orrát.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mb-mosquito-bite.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>Az új koronavírus terjedhet szúnyogcsípéssel?</h3>
      <p>
        A mai napig nem állnak rendelkezésre adatok vagy bizonyítékok arra
        vonatkozóan, hogy az új koronavírust szúnyogok terjeszthetik. Az új
        koronavírus légúti vírus, amely elsősorban olyan cseppeken keresztül
        terjed, amelyek egy fertőzött személy köhögéskor vagy tüsszentéskor
        keletkeznek, vagy nyál- vagy orrfolyáson keresztül. Saját magának a
        védelme érdekében gyakran tisztítsa meg a kezét alkoholos alapú
        kéztisztítóval, dörzsölje le vagy mossa le szappannal és vízzel.
        Ezenkívül kerülje a szoros kapcsolatot mindenkivel, aki köhög és
        tüsszent.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbusters-27.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>A kézszárítók hatékonyan megölik az új koronavírust?</h3>
      <p>
        Nem. A kézszárítók nem hatékonyak a 2019-nCoV elpusztításában. Annak
        érdekében, hogy megvédje magát az új koronavírus ellen, gyakran meg kell
        tisztítania a kezét alkohol alapú kézmosással, vagy mossuk le szappannal
        és vízzel. Miután megtisztította a kezét, alaposan szárítsa meg
        papírtörlővel vagy kézszárítóval.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbusters-31.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>Az ultraibolya fertőtlenítő lámpa megöli az új koronavírust?</h3>
      <p>
        Az ultraibolya lámpákat nem szabad a kéz vagy a bőr más részeinek
        sterilizálására használni, mivel az ultraibolya sugárzás bőrirritációt
        okozhat.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbusters-25.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Mennyire hatékonyak a hőszkennerek az új koronavírussal fertőzött
        emberek kimutatására?
      </h3>
      <p>
        A hőszkennerek hatékonyan felismerik azokat az embereket, akiknél láz
        jelentkezett (azaz a normálnál magasabb a testhőmérséklet) az új
        koronavírus fertőzése miatt. Ugyanakkor nem tudják kimutatni a fertőzött
        embereket, akik nem lázasok. Ennek oka az, hogy 2-10 napig tart, amíg a
        fertőzött emberek megbetegednek és láz alakul ki.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbusters-33.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Az alkohol vagy a klór permetezése az egész testre elpusztíthatja az új
        koronavírust?
      </h3>
      <p>
        Nem. Az alkohol vagy a klór permetezése az egész testre nem pusztítja el
        a testbe már bekerült vírusokat. Az ilyen anyagok permetezése káros
        lehet a ruhára vagy a nyálkahártyára (azaz a szemre, a szájra). Vegye
        figyelembe, hogy mind az alkohol, mind a klór hasznos lehet a felületek
        fertőtlenítésében, ám ezeket megfelelő ajánlások szerint kell használni.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/who/11.png" alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>A pneumonia elleni oltások védenek-e az új koronavírustól?</h3>
      <p>
        Nem. A pneumonia elleni oltások, például a pneumokokkusz oltás és a
        Haemophilus influenza B típusú (Hib) oltás nem nyújtanak védelmet az új
        koronavírus ellen. A vírus annyira új és különböző, hogy új oltására van
        szükség. A kutatók a 2019-nCoV elleni oltást próbálják kidolgozni, és a
        WHO támogatja erőfeszítéseiket. Bár ezek az oltások nem hatásosak a
        2019-nCoV ellen, egészségének védelme érdekében erősen ajánlott a
        légzőszervi betegségek elleni oltás.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/who/23.png" alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Rendszeresen öblítheti az orrát sóoldattal az új koronavírus
        fertőzésének megelőzésére?
      </h3>
      <p>
        Nem. Nincs bizonyíték arra, hogy az orr sóoldattal történő rendszeres
        öblítése megvédené az embereket az új koronavírus fertőzésektől. Kevés
        korlátozottElégtelen bizonyíték van arra, hogy az orr sóoldattal történő
        rendszeres öblítése segíthet az embereknek gyorsabban felépülni a
        megfázásból. Az orr rendszeres öblítése azonban nem bizonyítja a légúti
        fertőzések megelőzését.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/who/19.png" alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        A fokhagyma evése segíthet megakadályozni az új koronavírus fertőzését?
      </h3>
      <p>
        A fokhagyma egy egészséges élelmiszer, amelynek lehetnek bizonyos
        antimikrobiális tulajdonságai. A jelenlegi azonban nincs bizonyíték
        arra, hogy a fokhagyma fogyasztás megvédené az embereket az új
        koronavírustól.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbuster-2.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Az új koronavírus az idősebb embereket érinti-e, vagy a fogékonyak-e a
        fiatalabb emberek is?
      </h3>
      <p>
        Az új koronavírussal (2019-nCoV) minden életkorú ember megfertőződhet.
        Az idős emberek és a korábban fennálló egészségügyi problémákkal küzdő
        emberek (például asztma, cukorbetegség, szívbetegség) érzékenyebbnek
        tűnnek a vírus súlyos megbetegedése esetén. A WHO azt javasolja, hogy
        minden életkorú ember tegyen lépéseket a vírus elleni védekezésre,
        például a jó kézhigiénia és a jó légzési higiénia betartásával.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbuster-3.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Hatékonyak-e az antibiotikumok az új koronavírus megelőzésére és
        kezelésére?
      </h3>
      <p>
        Nem, az antibiotikumok nem működnek a vírusok ellen, csak baktériumokkal
        szemben hatékonyak. Az új koronavírus (2019-nCoV) vírus, ezért az
        antibiotikumok nem használhatók megelőzés vagy kezelés eszközeként. Ha
        azonban a 2019-nCoV miatt kórházba kerülnek, akkor antibiotikumokat
        kaphatnak, mivel fennálhat bakteriális felülfertőzés.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img
        src="../img/who/mythbuster-4.png"
        alt="who myth-busters coronavirus image" />
    </div>
    <div class="text-container">
      <h3>
        Van-e speciális gyógyszer az új koronavírus megelőzésére vagy
        kezelésére?
      </h3>
      <p>
        A mai napig nem javasoltak speciális gyógyszert az új koronavírus
        (2019-nCoV) megelőzésére vagy kezelésére. Mindazonáltal a vírussal
        fertőzött személyeknek megfelelő ellátást kell kapniuk a tünetek
        enyhítésére és kezelésére, a súlyos betegségben szenvedőkre pedig
        optimalizált támogató kezelést kell kapniuk. Néhány speciális kezelést
        vizsgálnak és klinikai vizsgálatok során tesztelnek. A WHO elősegíti a
        kutatási és fejlesztési erőfeszítések felgyorsítását számos partnerrel.
      </p>
    </div>
  </div>
  <span>
    *Forrás:
    <a
      href="https://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/myth-busters">
      WHO
    </a>
  </span>
</section>
