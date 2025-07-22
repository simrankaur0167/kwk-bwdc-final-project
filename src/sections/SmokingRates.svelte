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
        text: "Smoking rates by county",
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
            text: "% of adults who smoke",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "% of adults who smoke",
            data: [
                { name: "Manhattan", y: 9.8 },
                { name: "Tompkins", y: 8.9 },
                { name: "Westchester", y: 5.6 },
                { name: "Chenango", y: 28.5, color: "#8c0d0b" },
                { name: "Wyoming", y: 22.3, color: "#8c0d0b" },
                { name: "Orleans", y: 14.9, color: "#8c0d0b" },
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
                They may also be exposed to less secondhand smoke, as smoking rates are lower in these areas.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/prevention/tobacco_control/reports/statshots/volume15/n2_smoking_among_adults.pdf">New York State Department of Health</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>