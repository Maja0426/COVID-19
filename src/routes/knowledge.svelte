<script>
  // These values are bound to properties of the video
  let time = 0;
  let duration;
  let paused = true;

  let showControls = true;
  let showControlsTimeout;

  function handleMousemove(e) {
    // Make the controls visible, but fade out after
    // 2.5 seconds of inactivity
    clearTimeout(showControlsTimeout);
    showControlsTimeout = setTimeout(() => (showControls = false), 2500);
    showControls = true;

    if (!(e.buttons & 1)) return; // mouse not down
    if (!duration) return; // video not loaded yet

    const { left, right } = this.getBoundingClientRect();
    time = (duration * (e.clientX - left)) / (right - left);
  }

  function handleMousedown(e) {
    // we can't rely on the built-in click event, because it fires
    // after a drag — we have to listen for clicks ourselves

    function handleMouseup() {
      if (paused) e.target.play();
      else e.target.pause();
      cancel();
    }

    function cancel() {
      e.target.removeEventListener("mouseup", handleMouseup);
    }

    e.target.addEventListener("mouseup", handleMouseup);

    setTimeout(cancel, 200);
  }

  function format(seconds) {
    if (isNaN(seconds)) return "...";

    const minutes = Math.floor(seconds / 60);
    seconds = Math.floor(seconds % 60);
    if (seconds < 10) seconds = "0" + seconds;

    return `${minutes}:${seconds}`;
  }
</script>

<style>
  div {
    position: relative;
  }

  /*  section {
    padding-bottom: 0;
  } */

  .controls {
    position: absolute;
    top: 0;
    width: 100%;
    transition: opacity 1s;
  }

  .info {
    display: flex;
    width: 100%;
    justify-content: space-between;
  }

  span {
    padding: 0.2em 0.5em;
    color: #000;
    font-size: 0.9em;
    background: #fff;
    /* opacity: 0.7; */
    border: 1px solid #fff;
    border-radius: 15px;
  }

  .time {
    width: 3em;
  }

  .time:last-child {
    text-align: right;
  }

  progress {
    display: block;
    width: 100%;
    height: 10px;
    -webkit-appearance: none;
    appearance: none;
  }

  progress::-webkit-progress-bar {
    background-color: rgba(0, 0, 0, 0.2);
  }

  progress::-webkit-progress-value {
    background-color: rgba(255, 255, 255, 0.6);
  }

  video {
    width: 100%;
  }
  /*===================7*/
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
    background: url("../img/virus1.jpg") no-repeat center/cover;
  }

  .sub-title {
    font-size: 2.5em;
    text-align: center;
    margin-bottom: 1em;
  }

  h3 ul li {
    line-height: 1.6;
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

  .text-container a {
    color: #3232ff;
  }

  .text-container a:hover {
    text-decoration: underline;
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

    .sub-title {
      font-size: 1.8em;
    }
    span {
      font-size: 0.8em;
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
    h1 {
      font-size: 3em;
    }

    span {
      font-size: 0.5em;
    }
  }
</style>

<svelte:head>
  <title>Balassagyarmat Koronavírus | Tudástár</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Tudástár - mit, miért, hogyan</h1>
    <h3>Koronavírus-betegség (COVID-19) tanácsok a lakosság számára</h3>
  </div>
</div>

<section>
  <h2 class="sub-title">
    Új tájékoztató videó a koronavírus elleni védekezésről
  </h2>
  <div>
    <video
      poster="../img/tajekoztato.jpg"
      src="../video/tajekoztato.mp4"
      on:mousemove={handleMousemove}
      on:mousedown={handleMousedown}
      bind:currentTime={time}
      bind:duration
      bind:paused />

    <div class="controls" style="opacity: {duration && showControls ? 1 : 0}">
      <progress value={time / duration || 0} />

      <div class="info">
        <span class="time">{format(time)}</span>
        <span>
          bal egérgomb kattintás hogy {paused ? 'elindítsd' : 'megállítsd'} /
          nyomvatartás a tekeréshez
        </span>
        <span class="time">{format(duration)}</span>
      </div>
    </div>
  </div>
</section>

<section>
  <h2 class="sub-title">Gyakran ismételt kérdések*</h2>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Mik azok a koronavírusok?</h3>
      <p>
        A nevüket az elektronmikroszkóppal látható, koronára emlékeztető,
        felszíni kitüremkedéseik alapján kapott koronavírus törzsek alapvetően
        az állatoknál fordulnak elő, némelyek képesek az emberben is fertőzést
        okozni. Az 1960-as évektől ismert kórokozóként ismert koronavírusok mind
        állatról emberre, mind emberről emberre terjedhetnek.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Mit kell tudni az újfajta koronavírusról?</h3>
      <p>
        Az új koronavírust (SARS-CoV-2) Kínában azonosították 2019 végén.
        Kezdetben 2019-nCoV (új koronavírus) névvel illették, majd az
        Egészségügyi Világszervezet (WHO) javaslatára SARS-CoV-2-re keresztelték
        a korábbi SARS-CoV-val (Severe Acute Respiratory Syndrome - súlyos
        heveny légúti tünetegyüttes vírusa) való rokonsága alapján. Az általa
        okozott betegséget COVID-19-nek (COVID: coronavirus disease -
        koronavírus okozta megbetegedés 2019) nevezik.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Mik a tünetei az új koronavírus által okozott megbetegedésnek?</h3>
      <p>
        Az újfajta koronavírus okozta megbetegedés leggyakrabban enyhe
        tünetekkel jár, láz, köhögés, légszomj, izomfájdalom és fáradékonyság
        jelentkezhetnek. Ritkábban súlyos kórforma alakulhat ki, ami
        tüdőgyulladással, heveny légzési elégtelenséggel, vagy akár szepszissel
        (vérmérgezés), keringési vagy több szervi elégtelenséggel járhat.
        Azoknál a betegeknél alakul ki gyakrabban súlyos, akár életveszélyes
        állapot, akik valamilyen krónikus alapbetegségben (magas vérnyomás,
        szív- és érrendszeri betegség, cukorbetegség, májbetegség, légzőszervi
        betegség, daganatos betegség) szenvednek.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Hogyan terjed az új koronavírus?</h3>
      <p>
        A vírus leginkább cseppfertőzéssel terjed: köhögéssel, tüsszentéssel,
        kilégzéssel kerül a környezetbe, majd a közelben tartózkodó másik
        emberre. Fertőzött felületek és tárgyak megérintésével a vírus a kézre
        kerülhet, az arc, a száj, az orr érintésével bejuthat a szervezetbe.
        Egyelőre nem ismert, hogy pontosan mennyi ideig marad fertőzőképes a
        vírus a felületeken, annyi azonban bizonyos, hogy az egyszerű
        fertőtlenítőszerek elpusztítják.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Hogy lehet gyógyítani az új koronavírus okozta megbetegedést?</h3>
      <p>
        Jelenleg nincs kezelési módja, gyógyszere. Enyhe esetekben a panaszok
        csillapítása a cél, súlyos állapotú betegnél az immunrendszert, a
        légzést, a keringést támogató kezeléseket alkalmaznak (pl.
        oxigénterápia, folyadékegyensúly helyreállítása, egyéb vírusok ellen
        korábban kifejlesztett gyógyszerek, szükség esetén légzéstámogatás).
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Van-e védőoltás az új koronavírus ellen?</h3>
      <p>
        A koronavírusok, így az új koronavírus ellen nincs védőoltás. Az új
        koronavírus esetében megkezdődött a vakcinafejlesztés, a védőoltás
        előállítása akár egy-másfél évig is eltarthat.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Mit tegyek a megelőzés érdekében?</h3>
      <p>
        A legfontosabb a gyakori és alapos szappanos kézmosás, vagy legalább 60%
        alkoholtartalmú kézfertőtlenítő használata. Különösen javasolt mosdó
        használatát követően és étkezés előtt! A maszk önmagában nem elegendő a
        fertőzés megállításához, ám viselése mások védelme érdekében javasolt,
        ha valaki légúti tünetektől szenved. Amennyiben valamilyen alapbetegsége
        (magas vérnyomás, cukorbetegség, szív- és érrendszeri betegség,
        légzőszervi betegség, májbetegség, daganatos betegség) van, saját
        védelme érdekében viseljen maszkot! Ha köhög vagy tüsszent, használjon
        papírzsebkendőt, azt használat után azonnal dobja ki a szemetesbe, majd
        mosson/fertőtlenítsen kezet!
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>A gyerekeket is érinti az új koronavírus okozta megbetegedés?</h3>
      <p>
        A vírussal bármilyen életkorú ember megfertőződhet, az eddig igazolt
        esetek között alig volt gyermekkorú beteg, aki betegsége enyhe lefolyású
        volt.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>
        Mi a teendő, ha azt gondolom, hogy az új koronavírussal fertőződtem?
      </h3>
      <p>
        Ha az új koronavírus okozta megbetegedés tüneteit tapasztalja és
        találkozott olyasvalakivel, akitől elkaphatta a fertőzést, minél
        hamarabb kérjen telefonos segítséget! A háziorvos, az ügyeletes orvos
        vagy a mentőszolgálat szakembere feltett kérdései megerősíthetik vagy
        kizárhatják a fertőzés gyanúját. Mindenképpen jelezze, ha ön vagy önnel
        kapcsolatban álló járt olyan országban az elmúlt két hétben, ahol új
        koronavírus-járvány zajlik.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>
        Mit tegyek, ha fertőzött területen jártam vagy olyasvalakivel
        érintkeztem, aki ott járt?
      </h3>
      <p>
        Ha a közelmúltban (14 napon belül) olyan országban járt, ahol új
        koronavírus-járvány zajlik, vagy kapcsolata volt valakivel, aki az
        érintett területről érkezett, és ezt követően a betegség tüneteit
        észleli magán, akkor haladéktalanul hívja fel háziorvosát, vagy a
        Nemzeti Népegészségügyi Központ ingyenesen hívható zöldszámai (
        <a href="tel:0680277455">06-80-277-455</a>
        vagy
        <a href="tel:0680277456">06-80-277-456</a>
        ) valamelyikét! Ha nem feltétlenül szükséges, emberek közé, orvosi
        váróba ne menjen, tömegközlekedést ne használjon, maradjon otthon!
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>
        Milyen fertőtlenítő szerek hatásosak az új koronavírussal szemben?
      </h3>
      <p>
        A koronavírusok hatástalanításához virucid (vírusölő) hatású
        fertőtlenítőszerek alkalmazhatók. Megfelelő az alapos, legalább 20
        másodpercig tartó, szappanos kézmosás, illetve alkoholos
        kézfertőtlenítők használata is. Felmosáshoz, takarításhoz is használjon
        fertőtlenítő tisztítószert! Szellőztessen gyakran!
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Az influenza elleni oltás véd az új koronavírus ellen?</h3>
      <p>
        Az influenza elleni oltás nem ad védettséget az új koronavírus okozta
        fertőzéssel szemben.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Mi történik, ha a fertőzés beigazolódik?</h3>
      <p>
        Amennyiben szállítható állapotban van, a beteget a mentőszolgálat a
        Dél-Pesti Centrumkórház - Országos Hematológiai és Infektológiai
        Intézetbe szállítja elkülönítés és további ellátás céljából.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Van-e lehetőség az új koronavírusra szűrővizsgálatot végeztetni?</h3>
      <p>
        Nincs. Jelenleg kizárólag akkor végezhető laboratóriumi kivizsgálás, ha
        a jellemző tünetek mutatkoznak, és a járványtani kockázat is fennáll.
        Tünetmentes emberek szűrővizsgálata, tesztelése nem indokolt.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>Várandós vagyok, mit tegyek a megelőzés érdekében?</h3>
      <p>
        Tartsa be a normál higiéniai rendszabályokat, ami influenza-szezonban
        egyébként is javasolt! Ide tartozik például a gyakori és alapos
        szappanos kézmosás, alkoholos kézfertőtlenítés. Tömegközlekedési
        eszközön történő utazáskor kerülje arca, szája, orra és szemei
        érintését! Jelenleg semmilyen adat nincs arról, hogy az új
        koronavírusnak magzatkárosító hatása lenne.
      </p>
    </div>
  </div>

  <div class="container">
    <div class="logo-container">
      <img src="../img/corona-logo.jpg" alt="covid19 logo" />
    </div>
    <div class="text-container">
      <h3>
        Szükséges-e tartós élelmiszereket nagyobb mennyiségben beszerezni?
      </h3>
      <p>
        A lakossági ellátás kiegyensúlyozott, a készletek biztosítják a
        kiskereskedelmi forgalomban esetlegesen, rövid időre jelentkező hiányok
        pótlását. Gondolja végig saját szükségleteit, és annak megfelelően
        intézze vásárlásait!
      </p>
    </div>
  </div>
  *Forrás:
  <a href="https://koronavirus.gov.hu/gyik">koronavirus.gov.hu</a>
</section>

<section>
  <h2 class="sub-title">Mikor kell maszkot használni*</h2>

  <ul>
    <li>
      Ha Ön egészséges, csak akkor csak akkor kell maszkot viselnie, ha olyan
      személlyel kerül kapcsolatba aki 2019-nCoV fertőzésgyanús.
    </li>
    <li>Viseljen maszkot, ha köhög vagy tüsszög.</li>
    <li>
      A maszkok csak akkor hatásosak, ha alkoholos alapú kézfertőtlenítő
      használatával vagy szappannal és vízzel történő gyakori kézmosással
      kombinálják.
    </li>
    <li>
      Ha maszkot visel, akkor tudnia kell hogyan kell használni és hogyan kell
      megfelelő módon ártalmatlanítani.
    </li>
    <li>
      A maszk felhelyezése előtt tisztítsa meg a kezét alkoholos
      kézfertőtlenítővel vagy alapos szappanos kézmosással.
    </li>
    <li>
      Fedje le a száját és az orrát maszkkal, és ellenőrizze, hogy nincs-e hézag
      az arc és a maszk között.
    </li>
    <li>
      Használat közben ne érintse meg a maszkot; ha igen, tisztítsa meg a kezét
      alkoholos kézfertítlenítővel vagy alapos szappanos kézmosással.
    </li>
    <li>
      Cserélje ki a maszkot egy újra, amint nedvessé válik és ne használja újra
      az egyszer használatos maszkokat.
    </li>
    <li>
      A maszk eltávolításához: vegye le hátulról (ne érintse meg a maszk
      elejét); azonnal dobja el egy zárt szemetesbe; tisztítsa meg a kezét
      alkoholos kézferőtlenítővel vagy alapos szappanos kézmosással.
    </li>
  </ul>
  *Forrás:
  <a
    href="https://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/myth-busters">
    WHO
  </a>
</section>
