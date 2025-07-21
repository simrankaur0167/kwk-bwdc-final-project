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
    "Access to education is extremely important, as it can promote upward social mobility and increase the chances of living a healthy, long, and satisfying life. To learn more or get involved, consider visiting the resources below! Together, we can ensure all New Yorkers have the opportunity to reach their full potential. ☺️";
  const citation =
    '<a href="https://equityinedny.edtrust.org/">New York Equity Coalition</a>, <a href="https://unitedwaynyc.org/programs/education/">United Way of New York City</a>, <a href="https://equityinedny.edtrust.org/">The Education Trust</a>';
</script>

<TextBox {text} {citation} />
