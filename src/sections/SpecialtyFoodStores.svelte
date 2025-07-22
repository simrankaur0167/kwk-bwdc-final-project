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
        text: "Density of specialty food stores by county",
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
            text: "Specialized food stores per 1,000 residents",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "# per 1,000 residents",
            data: [
                { name: "Manhattan", y: 0.26 },
                { name: "Tompkins", y: 0.1 },
                { name: "Westchester", y: 0.15 },
                { name: "Chenango", y: 0.04, color: "#8c0d0b" },
                { name: "Wyoming", y: 0.02, color: "#8c0d0b" },
                { name: "Orleans", y: 0.05, color: "#8c0d0b" },
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
                Compared to their peers in Orleans, Wyoming, and Chenango, they would have access to a diverse array of nutritious and well-prepared foods, as highly educated areas have a higher density of specialty food stores.
                <br /><br />
                Source: <a href="https://www.ers.usda.gov/data-products/food-environment-atlas/go-to-the-atlas">U.S. Department of Agriculture</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>