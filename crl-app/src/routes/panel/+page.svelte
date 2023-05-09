<script>
    import { page } from '$app/stores'
    import { onMount } from 'svelte';

console.log();
let socket
onMount(() => {
  socket = new WebSocket("ws://"+$page.url.searchParams.get('ip'))
  socket.addEventListener("open", ()=> {
    console.log("Opened")
  })
})

</script>

<div>
    
</div>