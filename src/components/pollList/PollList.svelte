<script>
  import { fade, slide, scale } from 'svelte/transition';
  import { flip } from 'svelte/animate';
  import PollStore from '../../stores/PollStore';
  import PollDetails from '../pollDetails/PollDetails.svelte';
</script>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <div in:fade out:scale|local animate:flip={{ duration: 500 }}>
      <PollDetails {poll} />
    </div>
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
