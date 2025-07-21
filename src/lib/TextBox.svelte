<script>
  import { onMount } from "svelte";
  let { text, citation } = $props();
  let cardElement;
  let isVisible = $state(false);

  onMount(() => {
    const observer = new IntersectionObserver(
      ([entry]) => {
        isVisible = entry.isIntersecting;
      },
      {
        root: null,
        rootMargin: "0px",
        threshold: 0.5,
      }
    );

    if (cardElement) {
      observer.observe(cardElement);
    }

    return () => {
      if (cardElement) observer.unobserve(cardElement);
    };
  });
</script>

<div
  class="text-card"
  class:in-view={isVisible}
  bind:this={cardElement}
>
  <div class="content">
    <p class="text">{text}</p>
    <p class="citation">{@html citation}</p>
  </div>
</div>

<style>
  .text-card {
    background-color: white;
    background-position: center;
    height: 75vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    box-sizing: border-box;
    font-family: Georgia, "Times New Roman", Times, serif;
    transition: background-color 0.5s ease;
  }

  .text-card.in-view {
    background-color: #feffe8;
  }

  .content {
    max-width: 1100px;
    padding: 5px;
    color: white;
  }

  .text {
    font-family: Georgia, "Times New Roman", Times, serif;
    font-size: 35px;
  }

  p {
    font-family: Georgia, "Times New Roman", Times, serif;
    color: black;
    font-size: 25px;
  }

  :global(a) {
    color: black;
  }

  :global(a:hover) {
    font-style: italic;
    color: black;
    text-decoration: underline;
  }
</style>
