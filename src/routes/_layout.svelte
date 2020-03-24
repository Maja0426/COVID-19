<script>
  import Nav from "../components/Nav.svelte";
  import Footer from "../components/Footer.svelte";
  import Scroll from "../components/Scroll.svelte";

  export let segment;
</script>

<style>
  main {
    width: 100%;
    background-color: #ffffff;
    color: #333;
    margin: 0;
    box-sizing: border-box;
  }
</style>

<Nav {segment} />

<main>
  <slot />
</main>
<Footer />
<Scroll {segment} />
