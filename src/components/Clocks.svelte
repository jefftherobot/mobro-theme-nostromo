<script>
  import { Radar } from 'svelte-chartjs';

  import {
    Chart as ChartJS,
    PointElement,
    RadialLinearScale,
    LineElement,
  } from 'chart.js';

  ChartJS.register(PointElement,RadialLinearScale,LineElement );

  let clear
  let chartRef
  let ms = 2000
  let clocks = [100, 255, 2300, 333, 5700, 4000, 1220, 900 ]

  let data = {
    labels: ['P-core 1','P-core 2','P-core 3','P-core 4','P-core 5','P-core 6','P-core 7','P-core 8'],
    datasets: [
      {
        label: 'CPU Clocks',
        borderColor: 'yellow',
        data: clocks,
      },
    ],
  };


  // const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;
  // const incr = () => (temp[0] = random(30,60) )


  // $: {
  //   clearInterval(clear)
  //   clear = setInterval(incr, ms)
  // }

</script>

<!-- <div class="label">
  <span>cpu</span>
  <span>{temp[0]}&#xb0;</span>
</div>

<div class="label">
  <span>gpu</span>
  <span>{temp[0]}&#xb0;</span>
</div>

<div class="label">
  <span>ambient</span>
  <span>{temp[0]}&#xb0;</span>
</div>

<div class="label">
  <span>water</span>
  <span>{temp[0]}&#xb0;</span>
</div>
<div class="label">
  <span>delta </span>
  <span>{temp[0]}&#xb0;</span>
</div> -->

<div class="chart-container">
  <Radar 
    bind:chart={chartRef} 
    {data}
    options={{
       scales: { 
        r: {
          suggestedMin: 0,
          suggestedMax: 6000,
          ticks: {
            textStrokeColor: 'rgb(54, 162, 235)',
            color: 'rgba(240, 240, 240, 0.5)',
            backdropColor: 'black'
          },
          grid: {
            color: "lightgreen",
          },
        }
      },
      elements: {
        line: {
          borderWidth: 1
        }
      },
      responsive: true,
      maintainAspectRatio: false }} />
</div>


<style>
  .label {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin: 0 auto;
    padding: 4px 0;
    text-align: left;
    font-size: 1.5em;
    width: 150px;
  }

  .label>span:nth-child(2){
    text-align: right;
  } 

  .chart-container {
    margin: 0 0 10px;
    width: 300px;
    height: 300px;
  }

</style>