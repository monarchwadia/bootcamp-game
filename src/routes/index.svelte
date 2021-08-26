<script>
const deck = [
  {
    label: "Ate junk food",
    happiness: 1,
    cash: -1_00,
    health: -1
  }
];

let health = 100;
let happiness = 30;
let cash = 10_00;
let hand = [];

for(let i = 0; i < 5; i++) {
  const randomCard = deck[0]
  hand.push(randomCard)
}

function playCard(card) {
  happiness += card.happiness
  cash += card.cash
  health += card.health
}
</script>

<h1>Bootcamp Card Game</h1>
<div class="wrapper">
  <button on:click={() => happiness++}>Happiness++</button>
  <button on:click={() => cash++}>Cash++</button>
  <div>
    {happiness}
    {cash}
  </div>
  <div>
    {#each hand as handCard}
      <div on:click={() => playCard(handCard)}>{handCard.label}</div>
    {/each}
  </div>
</div>
<style>
.wrapper {
  /* background-color: black; */
  display: flex;
  flex-direction: column;
}
</style>