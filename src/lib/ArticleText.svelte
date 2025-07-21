<script>
    let { children } = $props();
    import { onMount } from "svelte";
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
        threshold: 1,
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
  class="article-text"
  class:in-view={isVisible}
  bind:this={cardElement}
>
  <p>{@render children()}</p>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 60%;
        background-color: white;
        color: black;
        border: solid black 3px;
        padding: 20px;
        font-family: Georgia, "Times New Roman", Times, serif;
        font-weight: normal;
        font-size: 20px;
    }

    .article-text.in-view {
    background-color: #feffe8;
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
