<script>
  import { createEventDispatcher } from "svelte";
  import { fly, fade } from "svelte/transition";

  export let title;

  const dispatch = createEventDispatcher();

  function closeModal() {
    dispatch("cancel");
  }
</script>

<style>
  .modal-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    z-index: 10;
  }

  .modal {
    position: fixed;
    top: 15vh;
    left: 5%;
    width: 90%;
    max-height: 80vh;
    background: white;
    /* background-image: var(--stripe); */
    z-index: 100;
    overflow: auto;
  }

  h1 {
    padding: 1rem;
    margin: 0;
    border-bottom: 1px solid #ccc;
    font-family: "Roboto Slab", sans-serif;
  }

  .content {
    padding: 1rem;
  }

  footer {
    padding: 1rem;
  }

  @media (min-width: 768px) {
    .modal {
      width: 40rem;
      left: calc(50% - 20rem);
    }
  }
</style>

<div transition:fade class="modal-backdrop" on:click={closeModal} />
<div transition:fly={{ y: 300 }} class="modal">
  <h1>{title}</h1>
  <div class="content">
    <slot />
  </div>
  <footer>
    <slot name="footer">
      <button on:click={closeModal}>Close</button>
    </slot>
  </footer>
</div>
