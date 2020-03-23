<script>
  import * as animateScroll from "svelte-scrollto";

  export let segment;

  let x;
  let scon = false;

  function scroller(event) {
    x = window.scrollY;
    if (x > 400) {
      scon = true;
    } else {
      scon = false;
    }
  }
</script>

<style>
  a {
    text-decoration: none;
  }

  svg {
    fill: #fff;
    width: 35px;
  }

  a:hover {
    cursor: pointer;
  }

  .top {
    display: none;
    position: fixed;
    right: 0;
    bottom: 0;
    background: #c31f09;
    opacity: 0.7;
    background-image: var(--stripe);
    color: #fff;
    padding: 0 10px;
  }

  .visible {
    display: block;
  }

  @media (max-width: 768px) {
    svg {
      fill: #fff;
      width: 30px;
    }
  }
</style>

<svelte:window on:scroll={scroller} />

<a
  on:click={() => animateScroll.scrollToTop()}
  class={scon === true ? 'top visible' : 'top'}
  href={segment === undefined ? '#top' : segment + '#top'}
  role="button"
  aria-label="Kezdőoldalra ugrás">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512">
    <path
      d="M177 159.7l136 136c9.4 9.4 9.4 24.6 0 33.9l-22.6 22.6c-9.4 9.4-24.6
      9.4-33.9 0L160 255.9l-96.4 96.4c-9.4 9.4-24.6 9.4-33.9 0L7
      329.7c-9.4-9.4-9.4-24.6 0-33.9l136-136c9.4-9.5 24.6-9.5 34-.1z" />
  </svg>
</a>
