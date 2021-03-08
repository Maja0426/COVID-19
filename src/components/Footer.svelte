<style>
  section {
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 0;
    background: #222;
    color: #fff;
  }

  .main-sub-footer,
  .sub-footer-links {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  .main-sub-footer {
    padding: 5px;
  }

  .main-sub-footer .col {
    margin: 1%;
  }

  .main-sub-footer p,
  .sub-footer-links p {
    margin: 2px;
    font-size: 18px;
  }
  .col {
    display: flex;
    width: 30%;
    margin: 1% 10%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .links {
    text-align: center;
  }

  .face-logo img {
    width: 48px;
  }

  hr {
    all: initial;
    background-color: #02a3dd;
    height: 1px;
    width: 50%;
    margin: 0 auto;
    margin: 0 auto;
  }

  hr:nth-of-type(2) {
    margin-bottom: 50px;
  }

  .sub-footer-links a {
    display: inline-block;
    text-decoration: none;
    color: #02a3dd;
    padding: 5px 10px;
    margin-bottom: 10px;
    margin-top: 20px;
    text-align: center;
  }

  .sub-footer-links a:hover {
    text-decoration: underline;
  }

  .col p a {
    text-decoration: none;
    color: #02a3dd;
    line-height: 2;
  }

  .col p a:hover {
    cursor: pointer;
    text-decoration: underline;
  }

  .smartbee-footer {
    display: flex;
    flex-direction: column;
    width: 100%;
    background: #222;
    padding: 20px 0;
  }

  .smartbee-footer a {
    text-decoration: none;
    color: #02a3dd;
  }

  .smartbee-footer a:hover {
    cursor: pointer;
    text-decoration: underline;
  }

  .logos img {
    width: 350px;
  }

  .text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  span {
    color: #fdf9f3;
  }

  @media (max-width: 768px) {
    .main-sub-footer,
    .sub-footer-links {
      flex-direction: column;
    }

    .sub-footer-links a {
      margin-top: 0;
    }

    .smartbee-footer {
      padding: 25px 0;
    }

    .main-sub-footer .col {
      width: 90%;
    }

    .logos img {
    width: 350px;
  }

    .col a {
      width: 70vw;
    }
  }

  @media (max-width: 320px) {
    .smartbee-footer {
      flex-direction: row;
    }

    .logos img {
    width: 300px;
  }

    .smartbee-footer h5 {
      font-size: 16px;
      padding: 0 10px;
      text-align: center;
    }
  }
</style>

<section class="footer">

  <div class="main-sub-footer">
    <div class="col">
      <div class="logos">
        <img src="../img/vigyazzunk2.jpg" alt="vigyázzunk egymásra plakát" />
      </div>
    </div>
    <div class="col">
      <div class="links">
        <p>
          <a
            href="https://koronavirus.gov.hu/"
            target="_blank"
            rel="noreferrer">
            Kormányzati koronavírus oldal
          </a>
        </p>
        <p>
          <a
            href="https://www.arcgis.com/apps/opsdashboard/index.html#/bda7594740fd40299423467b48e9ecf6"
            target="_blank"
            rel="noreferrer">
            COVID-19 térkép
          </a>
        </p>
        <p>
          <a href="https://www.nnk.gov.hu/" target="_blank" rel="noreferrer">
            NNK - Nemzeti Népegészségügyi Központ
          </a>
        </p>
        <p>
          <a href="https://ec.europa.eu/info/live-work-travel-eu/coronavirus-response/safe-covid-19-vaccines-europeans/how-do-vaccines-work_hu" target="_blank" rel="noreferrer">
            Hogyan hatnak a védőoltások?
          </a>
        </p>
      </div>
    </div>
    <div class="col">
      <div class="logos">
        <img src="../img/reg_javitas.jpg" alt="elrontott oltási regisztráció javítási lehetőségéről plakát" />
      </div>
    </div>

  </div>

  <div class="sub-footer-links">
    <p class="face-logo">
      <a
        href="https://www.facebook.com/smartbeeweb"
        target="_blank"
        rel="noreferrer"
        title="Smartbee Web Balassagyarmat">
        <img src="../img/facebook.svg" alt="facebook logo" />
      </a>
    </p>
  </div>

  <div class="sub-footer-links">

    <p>
      <a href="impressum" rel="noreferrer">Impresszum</a>
    </p>
    <p>
      <a href="cooky" rel="noreferrer">Sütik</a>
    </p>
  </div>
<hr>
  <div class="smartbee-footer">
    <div class="text">
      <h5>
        &copy; COPYRIGHT 2018-2020.
        <a href="https://smartbeeweb.hu" target="_blank" rel="noreferrer">
          SMART-BEE WEB
        </a>
      </h5>
      <h5>
        | All Right Reserved | POWERED BY
        <span>SVELTE / SAPPER</span>
        |
      </h5>
    </div>
  </div>
  <hr>
</section>
