<script>
const COST_TO_DISCARD = -1; // happiness

const deck = [
  {
    label: "Ate junk food",
    happiness: 1,
    cash: -1_00,
    health: -1,
    flavor: "You just couldn't resist, could you?"
  }
];

let health = 100;
let happiness = 30;
let cash = 10_00;
let hand = [];
let discardPile = [];

for(let i = 0; i < 5; i++) {
  const randomCard = deck[0]
  hand.push({...randomCard})
}

function playCard(card) {
  happiness += card.happiness
  cash += card.cash
  health += card.health
  hand = hand.filter(c => c !== card)
  discardPile = [...discardPile, card]
}

// function discardCard(card) {
//   hand = hand.filter(c => c !== card)
// }
</script>

<h1>Bootcamp Card Game</h1>
<div class="wrapper">
  <button on:click={() => happiness++}>Happiness++</button>
  <button on:click={() => cash++}>Cash++</button>
  <div>
    {happiness}
    {cash}
  </div>
  <div class="hand-wrapper">
    {#each hand as card}
      <div on:click={() => playCard(card)} class="card">
        <div class="label">{card.label}</div>
        <div class="description"></div>
        <div class="costs">
          <div class="health">Health: {card.health}</div>
          <div class="happiness">Happiness: {card.happiness}</div>
          <div class="cash">Cash: {card.cash} ¢</div>
          <div class="flavor">{card.flavor}</div>
        </div>
      </div>
    {/each}
  </div>
  <div class="discard-pile-wrapper">
    {#each discardPile as card}
      <div class="card">
        <div class="label">{card.label}</div>
        <div class="flavor">{card.flavor}</div>
      </div>
    {/each}
  </div>
</div>
<style>
.wrapper {
  /* background-color: black; */
  display: flex;
  flex-direction: column;
}

.hand-wrapper {
  display: flex;
  flex-direction: row;
  gap: 30px;
}

.hand-wrapper .card {
  display: flex;
  flex-direction: column;
  border: 1px solid rgb(97, 77, 64);
  width: 150px;
  height: 200px;
}

.discard-pile-wrapper {
  display: flex;
  flex-direction: row ;
}
.discard-pile-wrapper .card {
  font-size: 0.8em;
  display: flex;
  flex-direction: column;
  border: 1px solid rgb(97, 77, 64);
  width: 75px;
  height: 100px;
}
</style>