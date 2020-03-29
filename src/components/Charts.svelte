<script>
  import { scaleLinear } from "d3-scale";
  export let comment = "";
  export let perc = [];
  export let coordinateX = [];
  export let coordinateY = [];
  export let barColor = "#c31f09";
  export let barBorder = "none";

  const points = [
    { year: coordinateX[0], percentage: perc[0] },
    { year: coordinateX[1], percentage: perc[1] },
    { year: coordinateX[2], percentage: perc[2] },
    { year: coordinateX[3], percentage: perc[3] },
    { year: coordinateX[4], percentage: perc[4] },
    { year: coordinateX[5], percentage: perc[5] },
    { year: coordinateX[6], percentage: perc[6] },
    { year: coordinateX[7], percentage: perc[7] },
    { year: coordinateX[8], percentage: perc[8] },
    { year: coordinateX[9], percentage: perc[9] },
    { year: coordinateX[10], percentage: perc[10] },
    { year: coordinateX[11], percentage: perc[11] },
    { year: coordinateX[12], percentage: perc[12] },
    { year: coordinateX[13], percentage: perc[13] },
    { year: coordinateX[14], percentage: perc[14] }
  ];

  const xTicks = [...coordinateX];
  const yTicks = [...coordinateY];
  const padding = { top: 20, right: 15, bottom: 20, left: 25 };

  let width = 500;
  let height = 200;

  function formatMobile(tick) {
    if (typeof tick === "string") {
      return tick.trim().slice(0, 10);
    } else {
      return "'" + (tick % 100);
    }
  }

  $: xScale = scaleLinear()
    .domain([0, xTicks.length])
    .range([padding.left, width - padding.right]);

  $: yScale = scaleLinear()
    .domain([0, Math.max.apply(null, yTicks)])
    .range([height - padding.bottom, padding.top]);

  $: innerWidth = width - (padding.left + padding.right);
  $: barWidth = innerWidth / xTicks.length;
</script>

<style>
  .chart {
    width: 100%;
    max-width: 800px;
    margin: 0.5em auto;
    margin-top: 4em;
    margin-bottom: 4em;
  }

  svg {
    position: relative;
    width: 100%;
    height: 350px;
  }

  .tick {
    font-family: Helvetica, Arial;
    font-size: 0.725em;
    font-weight: 200;
  }

  .tick line {
    stroke: #e2e2e2;
    stroke-dasharray: 2;
  }

  .tick text {
    fill: #4a4b4e;
    text-anchor: start;
  }

  .tick.tick-0 line {
    stroke-dasharray: 0;
  }

  .x-axis .tick text {
    text-anchor: middle;
  }

  .bars rect {
    opacity: 0.65;
  }
</style>

<div class="chart" bind:clientWidth={width} bind:clientHeight={height}>
  <svg>
    <!-- y axis -->
    <g class="axis y-axis" transform="translate(0,{padding.top})">
      {#each yTicks as tick}
        <g
          class="tick tick-{tick}"
          transform="translate(0, {yScale(tick) - padding.bottom})">
          <line x2="100%" />
          <text y="-4">
            {tick}
            {tick === coordinateY[coordinateY.length - 1] ? ` ${comment}` : ''}
          </text>
        </g>
      {/each}
    </g>

    <!-- x axis -->
    <g class="axis x-axis">
      {#each points as point, i}
        <g class="tick" transform="translate({xScale(i)},{height})">
          <text x={barWidth / 2} y="-7">
            {width > 380 ? point.year : formatMobile(point.year)}
          </text>
        </g>
      {/each}
    </g>

    <g class="bars">
      {#each points as point, i}
        <rect
          style="fill:{barColor}; stroke:{barBorder}"
          x={xScale(i) + 2}
          y={yScale(point.percentage)}
          width={barWidth - 4}
          height={height - padding.bottom - yScale(point.percentage)} />
      {/each}
    </g>
  </svg>
</div>
