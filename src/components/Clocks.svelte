<script>
  import { Link } from "svelte-navigator";
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


  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;
  const incr = () => (data.datasets[0].data[0]=random(100,6000),data.datasets[0].data[1]=random(100,6000),data.datasets[0].data[2]=random(100,6000),data.datasets[0].data[3]=random(100,6000),data.datasets[0].data[4]=random(100,6000),data.datasets[0].data[5]=random(100,6000),data.datasets[0].data[6]=random(100,6000),data.datasets[0].data[7]=random(100,6000),chartRef.update() )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

</script>
<Link to="../">[X]</Link>
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
            backdropColor: 'rgba(0,0,0,0)'
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
  .chart-container {
    margin: 0 0 10px;
    width: 400px;
    height: 400px;
  }

</style>