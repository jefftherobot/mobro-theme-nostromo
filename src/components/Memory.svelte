<script>
  import { Bar } from 'svelte-chartjs';
  import { Chart, BarElement, CategoryScale, LinearScale } from 'chart.js';

  let used = 4410.0
  let free = 28192.0
  let max = used + free;

  let data = {
    labels: [''],
    datasets: [
      {
        barThickness: 20,
        barPercentage: 1,
        data: [used],
      },
    ],
  };


  let chartRef;

  Chart.register(BarElement,CategoryScale,LinearScale);

  export function update(){ chartRef.update()}

</script>

<div class="label">
  <span>{data.datasets[0].data[0]}/{max}</span>
  <span>ram</span>
</div>

<div class="chart-container">
  <Bar 
    bind:chart={chartRef} 
    {data}
    options={{
      backgroundColor:"yellow", 
      indexAxis: 'y',
      scales: { 
        y:{ display:false, offset:false},
        x:{ display:false, suggestedMin: 0, suggestedMax: max}
      },
      responsive: true,
      maintainAspectRatio: false }} />
</div>

<div class="label">
  <span>{data.datasets[0].data[0]}/{max}</span>
  <span>vram</span>
</div>

<div class="chart-container">
  <Bar 
    bind:chart={chartRef} 
    {data}
    options={{
      backgroundColor:"yellow", 
      indexAxis: 'y',
      scales: { 
        y:{ display:false,offset:false},
        x:{ display:false, suggestedMin: 0, suggestedMax: max}
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
    margin: 0 0 10px;
    width: 300px;
    height: 10px;
  }

  .chart-container{
    border: 1px solid yellow;
  }

</style>