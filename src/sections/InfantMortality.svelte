<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        legend: {
    enabled: false,
    },
    chart: {
        type: "bar",
        style: {
            fontFamily: "Georgia, serif",
        },
    },
    title: {
        text: "Infant mortality rate",
    },
    plotOptions: {
        column: {
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
    xAxis: {
        type: "category",
    },
    yAxis: {
        title: {
            text: "Infant mortality rate",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "Infant mortality rate",
            data: [
                { name: "Manhattan", y: 2.8 },
                { name: "Tompkins", y: 1.4 },
                { name: "Westchester", y: 2.8 },
                { name: "Chenango", y: 6.3 },
                { name: "Wyoming", y: 8.4 },
                { name: "Orleans.", y: 0.0 },
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
                A child born in Manhattan, Tompkins, or Westchester has a higher chance of survival. Infant mortality rates are lower in highly educated counties.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/statistics/vital_statistics/2021/table45.htm">New York State Department of Health</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>