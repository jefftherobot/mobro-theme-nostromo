<script>
  import { Bar } from 'svelte-chartjs';
  import { Chart, BarElement, CategoryScale, LinearScale } from 'chart.js';

  export let unit;
  export let label;
  export let max;
  export let data;

  let chartRef;

  Chart.register(BarElement,CategoryScale,LinearScale);

  export function update(){ chartRef.update()}

</script>

<div class="label">
  <span>{data.datasets[0].data[0]}{unit}</span>
  <span>{label}</span>
</div>

<hr/>

<div class="chart-container">
  <Bar 
    bind:chart={chartRef} 
    {data}
    options={{
      backgroundColor:"yellow", 
      indexAxis: 'y',
      scales: { 
        y:{ display:false},
        x:{ display:false, suggestedMin: 0, suggestedMax: max }
      },
      responsive: true,
      maintainAspectRatio: false }} />
</div>

<style>
  .label {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 4px 0;
    text-align: left;
    font-size: 1em;
   
  }

  .label>span:nth-child(2){
    text-align: right;
  } 

  .chart-container {
    margin: 0 0 5px;
    width: 100%;
    height: 20px;
  }

</style>