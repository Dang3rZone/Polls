<script>
  import PollDetails from '../pollDetails/PollDetails.svelte';

  export let polls = [];
</script>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <PollDetails {poll} />
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
