<script>
  import BarGraph from './BarGraph.svelte';
  
  let value = 0;
  let max = 1200;

  let ms = 1000;
  let clear;

  let data = {
    labels: [''],
    datasets: [
      {
        data: [value],
      },
    ],
  };

  let cpuGraph;
  const random = (min, max) => Math.floor(Math.random() * (max - min)) + min;
  const incr = () => (data.datasets[0].data[0] = random(200,1200),cpuGraph.update() )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

 
</script>


<BarGraph bind:this={cpuGraph} {data} {max} label="pump" unit=" rpm" />
<BarGraph bind:this={cpuGraph} {data} {max} label="radiator" unit=" rpm" />
<BarGraph bind:this={cpuGraph} {data} {max} label="exhaust" unit=" rpm" />