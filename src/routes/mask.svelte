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
    background: url("../img/face-mask.jpg") no-repeat center/cover;
  }

  .sub-title {
    font-size: 2.5em;
    text-align: center;
    margin-bottom: 1em;
  }

  h3 ul {
    /* list-style: none; */
    padding: 1em;
    margin: 4em 0;
  }

  h3 ul li {
    line-height: 1.6;
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
  <title>Balassagyarmat Koronavírus | Tények-tévhitek</title>
</svelte:head>

<div class="main-bg-hero" id="top">
  <div class="main-title-hero">
    <h1>Maszk</h1>
    <h3>
      Koronavírus-betegség (COVID-19) tanácsok a lakosság számára: Mikor és
      hogyan kell maszkokat használni.
    </h3>
  </div>
</div>

<section>
  <h2 class="sub-title">Mikor kell maszkot használni</h2>
  <h3>
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
    </ul>
  </h3>

  <h2 class="sub-title">
    Hogyan kell felhelyezni, használni, levenni és ártalmatlanítani a maszkot
    (WHO video)
  </h2>
  <div>
    <video
      poster="../img/who-logo.png"
      src="../video/mask.mp4"
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

  <h3>
    <ul>
      <li>
        A maszk felhelyezése előtt tisztítsa meg a kezét alkoholos
        kézfertőtlenítővel vagy alapos szappanos kézmosással.
      </li>
      <li>
        Fedje le a száját és az orrát maszkkal, és ellenőrizze, hogy nincs-e
        hézag az arc és a maszk között.
      </li>
      <li>
        Használat közben ne érintse meg a maszkot; ha igen, tisztítsa meg a
        kezét alkoholos kézfertítlenítővel vagy alapos szappanos kézmosással.
      </li>
      <li>
        Cserélje ki a maszkot egy újra, amint nedvessé válik és ne használja
        újra az egyszer használatos maszkokat.
      </li>
      <li>
        A maszk eltávolításához: vegye le hátulról (ne érintse meg a maszk
        elejét); azonnal dobja el egy zárt szemetesbe; tisztítsa meg a kezét
        alkoholos kézferőtlrnítővel vagy alapos szappanos kézmosással.
      </li>
    </ul>
  </h3>
  *Forrás:
  <a
    href="https://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/myth-busters">
    WHO
  </a>
</section>
