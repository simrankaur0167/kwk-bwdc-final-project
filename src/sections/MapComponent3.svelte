<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <img class="map-img" src="map3.png" alt="Map of NYS showing outflow" />
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        If a resident of Orleans, Wyoming, or Chenango were to pursue higher education, they would most likely leave their county of origin. Upstate New York, which includes these counties, has one of the largest outflows of educated workers in the United States. This outflow perpetuates cycles of low educational attainment and poor health outcomes.
        <br /><br />
                Source: <a href="https://www.newyorkfed.org/medialibrary/media/research/regional_economy/glance/upstate_glance1_07.pdf">Federal Reserve Bank of New York</a>
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