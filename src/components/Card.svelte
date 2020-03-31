<script>
  import { onMount, onDestroy } from "svelte";

  const loaded = new Map();
  let visible = false;

  function lazy(node, data) {
    if (loaded.has(data.src)) {
      node.setAttribute("src", data.src);
    } else {
      // simulate slow loading network
      setTimeout(() => {
        const img = new Image();
        img.src = data.src;
        img.onload = () => {
          loaded.set(data.src, img);
          node.setAttribute("src", data.src);
        };
      }, 20);
    }

    return {
      destroy() {}
    };
  }

  onMount(() => {
    visible = true;
  });

  onDestroy(() => {
    visible = false;
  });
</script>

<style>
  .card {
    /* width: 30%; */
    max-width: 300px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: #fff;
    color: #000;
    margin: 1em;
    box-shadow: 2px 2px 5px #222;
  }

  .card img {
    width: 100%;
  }

  .card-logo,
  .card-body {
    display: flex;
    justify-content: center;
    /* padding: 5px; */
  }

  @media (max-width: 420px) {
    .card {
      width: 100%;
      margin: 1em 0;
      /* box-shadow: none; */
      border: 1px solid #ccc;
    }
  }
</style>

<div class="card">
  <slot name="logo">
    <div class="card-logo">
      <img alt="corona logo" use:lazy={{ src: '.././img/corona-logo4.jpg' }} />
    </div>
  </slot>
  <div class="card-body">
    <slot name="name" />
  </div>
</div>
