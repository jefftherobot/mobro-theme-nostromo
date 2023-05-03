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

  let clear
  let chartRef
  let ms = 2000
  let temp = 0
  let load = [20, 100]

  let data = {
    labels: ['CPU'],
    datasets: [
      {
        label: '%',
        data: load,
      },
    ],
  };


  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;
  const incr = () => (temp = random(30,60),load[0] = random(10,20),chartRef.update() )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

  
// console.log(MobroSDK)
// MobroSDK.init()
// MobroSDK.addChannelListener("general_processor_usage", (data) => {
//  //console.log('test',data.payload)
//     if(data.payload){
//         load[0]=Math.round(data.payload.value);
//         chartRef.update()
//     }else{
//        load[0]=0
//        chartRef.update()
//     }
// })
</script>

<div class="label">
  <!-- <span>{data.datasets[0].data[0]}% </span> -->
  <span>{load[0]}%</span>
  <span>cpu</span>
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
        x:{ display:false}
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
    width: 100px;
    height: 20px;
  }

</style>