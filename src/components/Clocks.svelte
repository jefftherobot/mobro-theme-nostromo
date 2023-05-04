<script>
  import { Bar } from 'svelte-chartjs';
  import { Chart, BarElement, CategoryScale, LinearScale } from 'chart.js';

  Chart.register(BarElement,CategoryScale,LinearScale);

  
  let clear
  let chartRef
  let ms = 1000
  let clocks = [255, 2300, 333, 5700, 4000, 1220, 200,100, 255, 230, 333, 570, 400, 1000, 900 ]
  let gpu_clock = [2000]

  let data = {
    labels: ['gpu','P-core 1','P-core 2','P-core 3','P-core 4','P-core 5','P-core 6','P-core 7','P-core 8','P-core 1','P-core 2','P-core 3','P-core 4','P-core 5','P-core 6','P-core 7','P-core 8'],
    datasets: [
      {
        label: 'CPU',
        borderColor: ['yellow'],
        data: clocks,
      }
    ],
  };


  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;

  function incr(){
    data.datasets[0].data[0]=random(100,4200)
    data.datasets[0].data[1]=random(100,3200)
    data.datasets[0].data[2]=random(100,5700)
    data.datasets[0].data[3]=random(100,1200)
    data.datasets[0].data[4]=random(100,1200)
    data.datasets[0].data[5]=random(100,1200)
    data.datasets[0].data[6]=random(100,1200)
    data.datasets[0].data[7]=random(100,1200)
    data.datasets[0].data[8]=random(100,1200)
    data.datasets[0].data[9]=random(100,1200)
    data.datasets[0].data[10]=random(100,1200)
    data.datasets[0].data[11]=random(100,1200)
    data.datasets[0].data[12]=random(100,1200)
    data.datasets[0].data[13]=random(100,1200)
    data.datasets[0].data[14]=random(100,1200)
    data.datasets[0].data[15]=random(100,1200)
    data.datasets[0].data[16]=random(4000,5000)
    chartRef.update() 
  }

  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

</script>

<div class="label">
  <span>cpu&nbsp;{data.datasets[0].data[1]}mhz <span style="color:green">gpu&nbsp;{data.datasets[0].data[0]}mhz</span> </span>
  <span></span>
</div>
<hr/>
<div class="chart-container">
  <Bar 
  bind:chart={chartRef} 
  {data}
  options={{
    backgroundColor:["yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","yellow","green"], 
    scales: { 
      y:{ display:false},
      x:{ display:false }
    },
    responsive: true,
    maintainAspectRatio: false }} />
</div>
<div>
  <span>cpu max&nbsp;{data.datasets[0].data[1]}mhz <span style="color:green">gpu max&nbsp;{data.datasets[0].data[0]}mhz</span> </span>
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