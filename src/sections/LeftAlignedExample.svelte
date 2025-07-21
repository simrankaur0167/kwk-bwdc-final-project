<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const options1 = {
    threshold: [0.85, 0.95],
  };

  const callback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 1) {
        // "active" state
        elem.style.backgroundColor = "#e3ff00";
      } else if (entry.intersectionRatio < 1) {
        // "inactive" state
        elem.style.backgroundColor = "#888888";
      }
    });
  };

    const series = [
        {
            name: "Group 1",
            data: [
                [1990, 3],
                [2000, 4],
                [2010, 1],
                [2020, 1],
            ],
            color: "#8427c9",
        },
        {
            name: "Group 2",
            data: [
                [1990, 2],
                [2000, 5],
                [2010, -2],
                [2020, 2],
            ],
            color: "#ff99fc",
        },
        {
            name: "Group 3",
            data: [
                [1990, 4],
                [2000, 3],
                [2010, 0],
                [2020, 3],
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = false;

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "Another Example Chart",
        },
        subtitle: {
            text: "With a subtitle! And styling!",
        },
        series: [series[0], series[1]],
    };

    function toggleThirdSeries() {
        const existingSeries = chart.series.find((s) => s.name === "Group 3");

        if (existingSeries) {
            existingSeries.remove();
            thirdSeriesVisible = false;
        } else {
            chart.addSeries(series[2]);
            thirdSeriesVisible = true;
        }
    }
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            <button on:click={toggleThirdSeries} class="toggle-button">
                {thirdSeriesVisible ? "Remove Group 3" : "Add Group 3"}
            </button>
            <div>
                <p>
                    You can use Svelte to add and remove data from a Highcharts
                    chart.
                </p>
                <p>
                    When you click the button above, a third group is toggled in
                    the chart. Check out the source code to see how it's done.
                </p>
                <p>
                    <strong
                        >🤔 How might you use other HTML elements, like
                        checkboxes or radio buttons, in a similar way to filter
                        data?</strong
                    >
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                A child born in Manhattan, Tompkins, or Westchester has a higher chance of survival. Infant mortality rates are lower in highly educated counties.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/statistics/vital_statistics/2021/table45.htm">New York State Department of Health</a>
            </ArticleText>

            <ArticleText>
                They will also be exposed to less secondhand smoke, as smoking rates are lower in these areas.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/prevention/tobacco_control/reports/statshots/volume15/n2_smoking_among_adults.pdf">New York State Department of Health</a>
            </ArticleText>

            <ArticleText>
                Compared to their peers in Orleans, Wyoming, and Chenango, they would have access to a diverse array of nutritious and well-prepared foods, as highly educated areas have a higher density of specialty food stores.
                <br /><br />
                Source: <a href="https://www.ers.usda.gov/data-products/food-environment-atlas/go-to-the-atlas">U.S. Department of Agriculture</a>
            </ArticleText>

            <ArticleText>
                Conversely, lower educated areas generally have a higher density of convenience stores, which mostly carry heavily processed, high calorie foods.
                <br /><br />
                Source: <a href="https://www.ncco.com/blog/foodservice-trends/how-convenience-stores-are-helping-fight-food-deserts/">National Checking Company</a>
            </ArticleText>

            <ArticleText>
                Children in highly educated areas will find their area’s largest city to be fairly walkable or bikeable, creating a natural environment for physical activity. Lower educated areas are primarily car-dependent.
                <br /><br />
                Source: <a href="https://www.walkscore.com/">Walk Score</a>
            </ArticleText>

            <ArticleText>
                Due to these factors, residents of lower educated areas have higher rates of diabetes and heart disease.
                <br /><br />
                Source: <a href="https://www.health.ny.gov/community/health_equity/reports/county/">New York State Department of Health</a>
            </ArticleText>

            <ArticleText>
                If a resident of Orleans, Wyoming, or Chenango were to pursue higher education, they would most likely leave their county of origin. Upstate New York, which includes these counties, has one of the largest outflows of educated workers in the United States. This outflow perpetuates cycles of low educational attainment and poor health outcomes.
                <br /><br />
                Source: <a href="https://www.newyorkfed.org/medialibrary/media/research/regional_economy/glance/upstate_glance1_07.pdf">Federal Reserve Bank of New York</a>
            </ArticleText>

            <ArticleText>
                Whether they become a finance bro/girlie in Manhattan, buy a cute suburban home by the Hudson in Westchester, or teach at Cornell in Tompkins County, they’re likely to enjoy smoke-free environments, a wider range of nutritious food options, and walkable communities—all of which contribute to longer life expectancy.
                <br /><br />
                Source: <a href="https://www.cdc.gov/nchs/nvss/usaleep/usaleep.html">Centers for Disease Control and Prevention - National Center for Health Statistics</a>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }

    .toggle-button {
        margin: 20px;
        padding: 20px;
        color: #007052;
        background-color: #0bd956;
        border: solid 2px #007052;
        border-radius: 16px;
        font-size: large;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 0 #007052;
    }

    .toggle-button:active {
        transform: translateY(2px);
        box-shadow: 0 2px 0 #007052;
    }
</style>
