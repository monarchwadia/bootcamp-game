<script>
let happiness = 100;
let cash = 10_00;
</script>

<h1>Bootcamp Card Game</h1>
<div class="wrapper">
  <button on:click={() => happiness++}>Happiness++</button>
  <button on:click={() => cash++}>Cash++</button>
  {happiness}
  {cash}
</div>
<style>
.wrapper {
  /* background-color: black; */
  display: flex;
  flex-direction: column;
}
</style>