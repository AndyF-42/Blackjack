<script lang="ts">
    export let suit: CardSuit;
    export let rank: CardRank;
    export let padding: any = 0;
</script>

<div class="main-card" style="--padding: {padding}">
    <img src="/svg-cards/{suit}_{rank}.svg" alt="{rank} of {suit}">
</div>

<style>
.main-card {
    padding-left: var(--padding);
}
</style>