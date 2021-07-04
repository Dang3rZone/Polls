<script>
  import PollStore from '../../stores/PollStore';
  import PollDetails from '../pollDetails/PollDetails.svelte';
</script>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <PollDetails {poll} on:vote />
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    gap: 1.5rem;
    grid-auto-rows: 22rem;
    grid-template-columns: repeat(auto-fill, minmax(15rem, 1fr));
  }
</style>
