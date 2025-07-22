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
        text: "Density of convenience stores by county",
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
            text: "Convenience stores per 1,000 residents",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "# per 1,000 residents",
            data: [
                { name: "Manhattan", y: 0.14 },
                { name: "Tompkins", y: 0.32 },
                { name: "Westchester", y: 0.26 },
                { name: "Chenango", y: 0.70, color: "#8c0d0b" },
                { name: "Wyoming", y: 0.47, color: "#8c0d0b" },
                { name: "Orleans", y: 0.34, color: "#8c0d0b" },
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
                Conversely, lower educated areas generally have a higher density of convenience stores, which mostly carry heavily processed, high calorie foods.
                <br /><br />
                Sources: <a href="https://www.ers.usda.gov/data-products/food-environment-atlas/go-to-the-atlas">U.S. Department of Agriculture</a>, <a href="https://www.ncco.com/blog/foodservice-trends/how-convenience-stores-are-helping-fight-food-deserts/">National Checking Company</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>