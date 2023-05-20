<script>
    import { page } from '$app/stores'
    import { onMount } from 'svelte';

console.log();
/**
     * @type {WebSocket}
     */
let socket;
onMount(() => {
  socket = new WebSocket("ws://"+$page.url.searchParams.get('ip'))
  socket.addEventListener("open", ()=> {
    console.log("Opened")
  })
})
let enabled = false;

/**
     * @param {string} btn
     */
function run(btn) {
  if (enabled){
    console.log("stop");
    enabled = false;
  }
  else{
    console.log(btn);
    socket.send(btn)
    enabled = true;
  }
}
</script>

<div class="ctr">
  <div class="kreis">
    <button on:click={() => run("RL")}>Grieties pa kreisi</button>
    <button on:click={() => run("ML")}>Braukt pa kreisi</button>
  </div>
    <div class="fb">
      <button on:click={() => run("FW")}>Uz priekšu</button>
      <button on:click={() => run("BW")}>Uz atpakaļu</button>
    </div>
    <div class="lab">
      <button on:click={() => run("RR")}>Grieties pa labi</button>
      <button on:click={() => run("MR")}>Braukt pa labi</button>
    </div>
</div>

<style>
  .fb{
    display: flex;
    flex-direction: column;
    width: 90px;
  }
  .lab{
    display: flex;
    flex-direction: column;
    width: 90px;
  }
  .kreis{
    display: flex;
    flex-direction: column;
    width: 90px;
  }
  .ctr{
    display: flex;
    flex-direction: row;
  }
</style>