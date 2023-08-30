<script lang="ts">
  import viteLogo from '/vite.svg'
  import Card from './lib/Card.svelte';
  
  interface Card {
    suit: CardSuit;
    rank: CardRank;
  };
  
  var hand: Array<Card> = [
    {rank: 1, suit: "spades"},
    {rank: 2, suit: "spades"},
    {rank: 3, suit: "spades"},
    {rank: 4, suit: "spades"},
  ];

  const deck: Array<Card> = [];
  for (let i = 0; i < 52; i++) {
    let suit: CardSuit = "spades";
    if (Math.floor(i / 13) == 1) {
      suit = "clubs";
    } else if (Math.floor(i / 13) == 2) {
      suit = "hearts";
    } else if (Math.floor(i / 13) == 3) {
      suit = "diamonds";
    }

    let rank: CardRank = i % 13 + 1 as CardRank;
    
    deck.push({
      suit: suit,
      rank: rank,
    });
  }
  
  function drawCard() {
    let card = deck.splice(Math.floor(Math.random() * deck.length), 1);
    hand = [...hand, ...card];
  }
  
</script>

<button on:click={drawCard}>Draw Card</button>

<div class="card-hand">
  {#each hand as card (card)}
    <Card {...card} padding="1em" />
  {/each}
</div>

<style>
.card-hand {
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>