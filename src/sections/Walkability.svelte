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
        text: "Walk score by largest city",
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
            text: "Walkability based on the distance to nearby places and pedestrian friendliness",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "Walk score",
            data: [
                { name: "Manhattan (NYC)", y: 88 },
                { name: "Tompkins (Ithaca)", y: 72 },
                { name: "Westchester (Yonkers)", y: 69 },
                { name: "Chenango (Greene)", y: 0, color: "#8c0d0b" },
                { name: "Wyoming (Bennington)", y: 0, color: "#8c0d0b" },
                { name: "Orleans", y: 25, color: "#8c0d0b" },
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
                <p>Both Greene in Chenango and Bennington in Wyoming have a walk score of 0, meaning all errands require a car.</p>
            </div>
        {/snippet}
        {#snippet scrolly()}
             <ArticleText>
                Children in highly educated areas will find their county’s largest city to be fairly walkable or bikeable, creating a natural environment for physical activity. Lower educated areas are primarily car-dependent.
                <br /><br />
                Source: <a href="https://www.walkscore.com/">Walk Score</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    p {
        font-family: Georgia;
    }
</style>