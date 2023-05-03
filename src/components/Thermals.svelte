<script>
  import { Doughnut } from 'svelte-chartjs';

  import {
    Chart as ChartJS,
    ArcElement,
    CategoryScale,
  } from 'chart.js';

  ChartJS.register(ArcElement, CategoryScale);

  let clear
  let chartRef
  let ms = 2000
  let temp = [45, 100]

  let data = {
    labels: ['CPU'],
    datasets: [
      {
        label: '%',
        data: temp,
      },
    ],
  };


  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;
  const incr = () => (temp[0] = random(30,60) )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

</script>

<div class="label">
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
    width: 100px;
    height: 100px;
  }

</style>