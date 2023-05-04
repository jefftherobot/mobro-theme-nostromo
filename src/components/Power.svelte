<script>
  import { Line } from 'svelte-chartjs';

  import {
    Chart as ChartJS,
    LineElement,
    LinearScale,
    PointElement,
    CategoryScale,
  } from 'chart.js';

  ChartJS.register( LineElement,LinearScale,PointElement,CategoryScale);

  let clear
  let chartRef
  let ms = 1000
  let cpu_watts = [83]
  let gpu_watts = [20]
  let val = 0
  let val2 = 0
  

  let data = {
    labels: ['1', '2', '3', '4', '5', '6', '7','8', '9', '10', '11', '12', '13', '14','15', '16', '17', '18', '19', '20', '21','22', '23', '24', '25', '26', '27', '28'],
    datasets: [
      {
        label: 'CPU',
        borderColor: 'yellow',
        data: cpu_watts,
      },{
        label: 'GPU',
        borderColor: 'green',
        data: gpu_watts,
      },
    ]
  };
  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;

  function incr(){
    if (data.datasets[0].data.length>=28){
      data.datasets[0].data.shift()
      data.datasets[1].data.shift()
    }

    data.datasets[0].data.push(random(1,200))
    data.datasets[1].data.push(random(1,200))
    val = data.datasets[0].data[data.datasets[0].data.length-1]
    val2 = data.datasets[1].data[data.datasets[1].data.length-1]
    chartRef.update('none')
  }

  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

</script>

<div class="label">
  <span>cpu&nbsp;{val}w gpu&nbsp;{val2}w</span>
  <span>Power</span>
</div>
<hr/>
<!-- 
<div class="label">
  <span>20w</span>
  <span>GPU</span>
</div>
<hr/> -->
<div class="chart-container">
  <Line 
    bind:chart={chartRef} 
    {data}
    options={{
       scales: { 
        y: {
          beginAtZero: true,
          suggestedMax: 250,
          ticks: {
            display: false,
          },
          grid: {
            color: '#9A9E1B',
            tickLength: 0
          }
        },
        x: {
          ticks: {
            display: false,
          },
          grid: {
            color: '#9A9E1B',
            tickLength: 0
          }
        },
      },
      elements: {
        line: {
          borderWidth: 1
        },
        point:{
          radius: 4,
          pointStyle: 'rectRot'
        }
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
    height: 120px;
  }

</style>