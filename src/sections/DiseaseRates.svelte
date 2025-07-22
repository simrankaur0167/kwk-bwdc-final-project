<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
  import { nonpassive } from "svelte/legacy";

    let options = {
  chart: {
    type: "column",
    style: {
      fontFamily: "Georgia, serif",
    },
  },
  title: {
    text: "Diabetes and heart disease by county",
  },
  xAxis: {
    categories: [
      "Manhattan",
      "Tompkins",
      "Westchester",
      "Chenango",
      "Wyoming",
      "Orleans",
    ],
    title: {
      text: "Counties",
    },
  },
  yAxis: {
    min: 0,
    title: {
      text: "Rate",
    },
  },
  plotOptions: {
    column: {
      grouping: true,
      dataLabels: {
        enabled: true,
        format: "{y}",
        style: {
          fontSize: "1em",
          textOutline: "none",
        },
      },
    },
  },
  series: [
    {
      name: "Diabetes hospitalizations per 1,000 residents",
      data: [
        { y: 174.3, color: "#34495e" },
        { y: 99.5, color: "#34495e" },
        { y: 157.3, color: "#34495e" },
        { y: 205.4, color: "#8c0d0b" },
        { y: 162.2, color: "#8c0d0b" },
        { y: 207.2, color: "#8c0d0b" },
      ],
    },
    {
      name: "Heart disease hospitalizations per 1,000 residents",
      data: [
        { y: 60.8, color: "#d3dce6" },
        { y: 41.4, color: "#d3dce6" },
        { y: 58.4, color: "#d3dce6" },
        { y: 80.4, color: "#f79a98" },
        { y: 73.1, color: "#f79a98" },
        { y: 82.1, color: "#f79a98" },
      ],
    },
  ],
};

</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div class="chart">
                <Chart {options} highcharts={Highcharts} />
            </div>
        {/snippet}
        {#snippet scrolly()}
             <ArticleText>
                Due to these factors, lower educated areas have more hospitalizations due to diabetes and heart disease.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/community/health_equity/reports/county/">New York State Department of Health</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>
