<div>

<div>
    <h1>Modris pilnīgā kontrolē</h1>

<div class="connect">
    <label for="ip">Modra I.P. adrese</label>
    <input id="ip" bind:value={ip}>
    
    <a href={"/panel?ip=" + ip}>Pievienoties</a>
</div>
</div>

</div>
<script>
    export let ip = "";
</script>

<style>
   
h1{
    color: white;
    font-family: Arial;
}
.connect{
color: white;
}
</style>