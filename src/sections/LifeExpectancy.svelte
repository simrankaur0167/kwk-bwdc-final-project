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
        text: "Life expectancy by county",
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
            text: "Average life expectancy in years",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "Average life expectancy in years",
            data: [
                { name: "Manhattan", y: 83.3 },
                { name: "Tompkins", y: 80.9 },
                { name: "Westchester", y: 82.1 },
                { name: "Chenango", y: 76.6, color: "#8c0d0b" },
                { name: "Wyoming", y: 78.9, color: "#8c0d0b" },
                { name: "Orleans", y: 77.5, color: "#8c0d0b" },
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
                Whether they become a finance bro/girlie in Manhattan, buy a cute suburban home by the Hudson in Westchester, or teach at Cornell in Tompkins, they’re likely to enjoy smoke-free environments, a wider range of nutritious food options, and walkable communities—all of which contribute to longer life expectancy.
                <br /><br />
                Source: <a href="https://www.cdc.gov/nchs/nvss/usaleep/usaleep.html">Centers for Disease Control and Prevention - National Center for Health Statistics</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>