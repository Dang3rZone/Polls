<script>
  import Header from './components/header/Header.svelte';
  import Footer from './components/footer/Footer.svelte';
  import Tabs from './ui/tabs/Tabs.svelte';
  import CreatePollForm from './components/createPoll/CreatePollForm.svelte';
  import PollList from './components/pollList/PollList.svelte';

  //tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';
  const tabChange = (e) => {
    activeItem = e.detail;
  };

  const handleAdd = (e) => {
    activeItem = 'Current Polls';
  };
</script>

<Header />
<main>
  <Tabs {items} {activeItem} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <PollList />
  {:else if activeItem === 'Add New Poll'}
    <CreatePollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
