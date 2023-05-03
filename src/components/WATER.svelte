<script>
  import { Bar } from 'svelte-chartjs';

  import {
    Chart,
    BarElement,
    CategoryScale,
    LinearScale,
  } from 'chart.js';

  Chart.register(
    BarElement,
    CategoryScale,
    LinearScale
  );

  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;

  let ms = 2000
  let temp = 0
  let load = [20, 100]
  const incr = () => (temp = random(30,60),load[0] = random(40,100),chartRef.update() )

  let clear
  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }
  let chartRef
  let data = {
  labels: ['CPU'],
  datasets: [
    {
      label: '%',
      data: load,
    },
  ],
};
</script>

<div class="label">
  <!-- <span>{data.datasets[0].data[0]}% </span> -->
  <span>{load[0]}%</span>
  <span>cpu</span>
</div>
<hr>
<Bar bind:chart={chartRef} {data} options={{  backgroundColor:"#e9ea73", indexAxis: 'y',scales: { y:{display:false},x:{display:false}},maintainAspectRatio: false }} />


<style>
  .label {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 4px;
    text-align: left;
   
  }

  .label>span:nth-child(2){
    text-align: right;
  } 

</style>