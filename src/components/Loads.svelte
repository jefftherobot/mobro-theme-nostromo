<script>
  import BarGraph from './BarGraph.svelte';
  
  let value = 0;
  let max = 100;

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
  const incr = () => (data.datasets[0].data[0] = random(20,40),cpuGraph.update() )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

 
</script>


<BarGraph bind:this={cpuGraph} {data} {max} label="cpu" unit="%" />
<BarGraph bind:this={cpuGraph} {data} {max} label="gpu" unit="%" />