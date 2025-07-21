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
        text: "Earnings by educational attainment",
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
            text: "Median usual weekly earnings in USD",
        },
    },
    series: [
        {
            color: "#34495e",
            name: "Earnings in USD",
            data: [
                { name: "Doctoral degree", y: 2083 },
                { name: "Professional degree", y: 2080 },
                { name: "Master's degree", y: 1661 },
                { name: "Bachelor's degree", y: 1432 },
                { name: "Associate's degree", y: 1005 },
                { name: "Some college, no degree", y: 935 },
                { name: "High school diploma", y: 853 },
                { name: "Less than a high school diploma", y: 682 },
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
                Behind this disparity is a gap in educational attainment. Adults with advanced degrees generally have higher salaries, which gives them access to high-cost-of-living areas. 
                <br /><br />
                Source: <a href="https://www.bls.gov/careeroutlook/2023/data-on-display/education-pays.htm">U.S. Bureau of Labor Statistics</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>