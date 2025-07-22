<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <img class="map-img" src="map1.png" alt="Map of NYS showing Orleans and Manhattan" />
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        In Manhattan, where 64% of adults aged 25 and older have a bachelor’s
        degree, the median home value is $1.16 million. In contrast, in Orleans
        County, where only 17.5% of adults aged 25 and older hold a bachelor’s
        degree, the median home value is $144,500.
        <br /><br />
        Sources:
        <a href="https://blackwealthdata.org/wealth-indicator"
          >Black Wealth Data Center - Wealth Indicators</a
        >,
        <a
          href="https://public.tableau.com/shared/C6P223WYT?:display_count=n&:origin=viz_share_link&:embed=y"
          >Black Wealth Data Center - Bachelor’s Degree Attainment: Local Level</a
        >,
        <a
          href="https://hdpulse.nimhd.nih.gov/data-portal/social/table?age=081&age_options=age25_1&demo=00006&demo_options=education_3&race=00&race_options=race_7&sex=0&sex_options=sexboth_1&socialtopic=020&socialtopic_options=social_6&statefips=36&statefips_options=area_states"
          >National Institute on Minority Health and Health Disparities</a
        >
      </ArticleText>

      <ArticleText
        >As a result of this divide, the lifestyles—and consequently, the health
        outcomes—of the most and least educated New Yorkers vary greatly.</ArticleText
      >
    {/snippet}
  </Scroller>
</div>

<style>
  .map-img {
    width: 150%;
    margin: 0px auto;
  }
</style>
