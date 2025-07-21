<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <img class="map-img" src="map2.png" alt="Map of NYS" />
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        To better understand this phenomenon, we can compare the three most
        educated counties—Manhattan (New York County), Tompkins, and
        Westchester—with the three least educated ones—Orleans, Wyoming, and
        Chenango.
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .map-img {
    width: 150%;
    margin: 0px auto;
  }
</style>
