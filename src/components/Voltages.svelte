<script>

  let clear
  let ms = 2000
  let vid = 1.29

  const random = (min, max) => Math.floor(Math.random() * (max - min)*100)/100 + min;
  const incr = () => (vid = random(.78,1.44) )


  $: {
    clearInterval(clear)
    clear = setInterval(incr, ms)
  }

</script>

<div class="label">
  <span>pcore-1</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-2</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-3</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-4</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-5</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-6</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-7</span>
  <span>{vid}V</span>
</div>
<div class="label">
  <span>pcore-8</span>
  <span>{vid}V</span>
</div>


<style>
  .label {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin: 0 auto;
    padding: 4px 0;
    text-align: left;
    font-size: 1.3em;
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