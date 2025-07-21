<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        chart: {
            type: "pie",
        },
        title: {
            text: "An Example Pie Chart",
        },
        plotOptions: {
            pie: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 20,
                    },
                    {
                        enabled: true,
                        distance: -40,
                        format: "{point.percentage:.1f}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                        },
                        filter: {
                            operator: ">",
                            property: "percentage",
                            value: 10,
                        },
                    },
                ],
            },
        },
        series: [
            {
                name: "Group",
                data: [
                    {
                        name: "Group 1",
                        y: 151,
                    },
                    {
                        name: "Group 2",
                        sliced: true,
                        selected: true,
                        y: 180,
                    },
                    {
                        name: "Group 3",
                        y: 32,
                    },
                    {
                        name: "Group 4",
                        y: 103,
                    },
                    {
                        name: "Group 5",
                        y: 77,
                    },
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
            <p>
                Here's an example chart using
                <a href="https://www.highcharts.com/">Highcharts</a>!
            </p>
            <p>
                📈 <strong>Highcharts</strong> is a super-flexible library for
                creating all kinds of charts. See demos of different chart types
                <a href="https://www.highcharts.com/demo">here</a>.
            </p>
            <p>
                Since we're using Highcharts through Svelte, the syntax is a
                little different from what you might see in the demos. But all
                of Highcharts' functionality is available through the Highcharts
                for Svelte package.
            </p>
            <p>
                The configuration is done through the
                <code>options</code> json object passed to the chart, which you'll
                see in the source code for this template.
            </p>
            <p>
                Use the
                <a href="https://api.highcharts.com/highcharts/"
                    >API reference</a
                >
                to understand what each element in the <code>options</code> object
                does.
            </p>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                Behind this disparity is a gap in educational attainment. Adults with advanced degrees generally have higher salaries, which gives them access to high-cost-of-living areas. 
                <br /><br />
                Source: <a href="https://www.bls.gov/careeroutlook/2023/data-on-display/education-pays.htm">U.S. Bureau of Labor Statistics</a>
            </ArticleText>

            <ArticleText>
                In Manhattan, where 64% of adults aged 25 and older have a bachelor’s degree, the median home value is $1.16 million. In contrast, in Orleans County, where only 17.5% of adults aged 25 and older hold a bachelor’s degree, the median home value is $144,500.
                <br /><br />
                Sources: <a href="https://blackwealthdata.org/wealth-indicator">Black Wealth Data Center - Wealth Indicators</a>, <a href="https://public.tableau.com/shared/C6P223WYT?:display_count=n&:origin=viz_share_link&:embed=y">Black Wealth Data Center - Bachelor’s Degree Attainment: Local Level</a>, <a href="https://hdpulse.nimhd.nih.gov/data-portal/social/table?age=081&age_options=age25_1&demo=00006&demo_options=education_3&race=00&race_options=race_7&sex=0&sex_options=sexboth_1&socialtopic=020&socialtopic_options=social_6&statefips=36&statefips_options=area_states">National Institute on Minority Health and Health Disparities</a>
            </ArticleText>

            <ArticleText>
                As a result of this divide, the lifestyles—and consequently, the health outcomes—of the most and least educated New Yorkers vary greatly.
            </ArticleText>

            <ArticleText>
                To better understand this phenomenon, we can compare the three most educated counties—Manhattan (New York County), Tompkins, and Westchester—with the three least educated ones—Orleans, Wyoming, and Chenango.
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }
</style>
