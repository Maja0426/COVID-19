<script>
  export let segment;
  let menu = false;

  function toggleMenu() {
    menu = !menu;
  }
</script>

<style>
  nav {
    display: flex;
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    width: 100%;
    height: 70px;
    background: #c31f09;
    background-image: var(--stripe);
    color: #fff;
    box-shadow: 1px 1px 7px rgb(46, 39, 39);
  }

  .hamburger {
    display: none;
  }

  .nav-links {
    margin-left: auto;
    margin-right: 1em;
  }

  .nav-links a:hover {
    background: #222;
    color: #fff;
    transition: 0.3s all ease-in;
  }

  .nav-links,
  .logo {
    display: flex;
    z-index: 100;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    padding: 0;
    list-style: none;
  }

  .nav-links li a {
    text-decoration: none;
    padding: 13px 0.8em;
    font-size: 16px;
    transition: 0.3s all ease-in;
  }

  .logo {
    padding: 7px;
    margin: 10px;
    font-weight: bold;
    text-decoration: none;
    transition: 0.3s all ease-in;
  }

  .logo:hover {
    cursor: pointer;
  }

  .logo img {
    height: 60px;
    border-radius: 50%;
  }

  /* clearfix */
  .nav-links::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 70px;
  }

  .selected {
    background: #222;
    background-image: var(--stripe);
    color: #fff;
  }

  @media (max-width: 768px) {
    .nav-links {
      justify-content: center;
      align-content: space-between;
      flex-direction: column;
      z-index: 100;
      margin-top: 70px;
      background: #333;
      color: #fff;
      position: fixed;
      height: calc(100vh - 70px);
      width: 100%;
      clip-path: circle(10% at 90% -10%);
      -webkit-clip-path: circle(10% at 90% -10%);
      transition: all 0.3s ease-out;
      pointer-events: none;
    }

    li {
      height: 50px;
    }

    .nav-links.open {
      clip-path: circle(150% at 90% -10%);
      -webkit-clip-path: circle(150% at 90% -10%);
      pointer-events: all;
    }

    .nav-links li a {
      padding: 0.3em 0.5em;
      font-size: 22px;
    }

    .hamburger {
      position: absolute;
      top: 50%;
      right: 3%;
      background: #c31f09;
      background-image: var(--stripe);
      color: #fff;
      z-index: 100;
      display: block;
      transform: translate(-5%, -50%);
    }

    .hamburger:hover {
      cursor: pointer;
    }

    .line {
      width: 35px;
      height: 4px;
      background-color: #fff;
      margin: 7px 0;
      transition: 0.2s;
      color: #fff;
    }

    .change .line:nth-child(1) {
      -webkit-transform: rotate(-45deg) translate(-9px, 7px);
      transform: rotate(-45deg) translate(-9px, 7px);
    }

    .change .line:nth-child(2) {
      opacity: 0;
    }

    .change .line:nth-child(3) {
      -webkit-transform: rotate(45deg) translate(-7px, -7px);
      transform: rotate(45deg) translate(-7px, -7px);
    }
  }
</style>

<nav>
  <a class="logo" href="." title="Főoldal">
    <img src="./img/corona-logo.jpg" alt="COVID19 logo" />
  </a>
  <div
    class={menu === false ? 'hamburger' : 'hamburger change'}
    on:click={toggleMenu}>
    <div class="line" />
    <div class="line" />
    <div class="line" />
  </div>

  <ul class={menu === false ? 'nav-links' : 'nav-links open'}>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        rel="prefetch"
        class={segment === 'blog' ? 'selected' : ''}
        href="blog">
        Hírek, információk
      </a>
    </li>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        class={segment === 'knowledge' ? 'selected' : ''}
        href="knowledge">
        Tudástár
      </a>
    </li>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        class={segment === 'facts' ? 'selected' : ''}
        href="facts">
        Tények és tévhitek
      </a>
    </li>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        class={segment === 'statistic' ? 'selected' : ''}
        href="statistic">
        Statisztikák
      </a>
    </li>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        class={segment === 'statistic' ? 'dentists' : ''}
        href="dentists">
        Fogovosi ügyelet
      </a>
    </li>
    <li>
      <a
        on:click={() => {
          menu = false;
        }}
        class={segment === 'disqus' ? 'selected' : ''}
        href="disqus">
        Fórum
      </a>
    </li>
  </ul>
</nav>
