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

  // polls
  let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },
  ];

  const handleAdd = (e) => {
    const poll = e.detail;
    polls = [poll, ...polls];

    activeItem = 'Current Polls';
  };
  // updating the votes
  const handleVote = (e) => {
    const { id, option } = e.detail;

    let copiedPolls = [...polls];
    let upvotedPoll = copiedPolls.find((poll) => poll.id === id);
    if (option === 'a') {
      upvotedPoll.votesA++;
    }
    if (option === 'b') {
      upvotedPoll.votesB++;
    }
    polls = copiedPolls;
  };
</script>

<Header />
<main>
  <Tabs {items} {activeItem} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <PollList {polls} on:vote={handleVote} />
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
