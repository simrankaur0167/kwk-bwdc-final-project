<script>
  import Scroller from "../lib/Scroller.svelte";
  import TextBox from "../lib/TextBox.svelte";

  const options = {
    threshold: [0.85, 0.95],
  };

  const callback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.3) {
        // "active" state
        elem.style.backgroundColor = "#e3ff00";
      } else if (entry.intersectionRatio < 0.3) {
        // "inactive" state
        elem.style.backgroundColor = "#888888";
      }
    });
  };

  const text =
    "New York State has one of the largest wealth disparities in the United States, with the top 5% of earners averaging $621,301 annually and the bottom 20% averaging $14,932.";
  const citation =
    'Source: <a href="https://www.nasdaq.com/articles/10-us-states-most-income-inequality">Nasdaq</a>';
</script>

<TextBox {text} {citation} />
