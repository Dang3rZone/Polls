<script>
  import { createEventDispatcher } from 'svelte';
  import PollStore from '../../stores/PollStore';

  import Button from '../../ui/button/Button.svelte';

  let dispatch = createEventDispatcher();
  let fields = { question: '', answerA: '', answerB: '' };
  let errors = { question: '', answerA: '', answerB: '' };
  let valid = false;

  const submitHandler = () => {
    valid = true;
    // validate question
    if (fields.question.trim().length < 5) {
      valid = false;
      errors.question = 'Question must be at least 5 characters long';
    } else {
      errors.question = '';
    }
    // validate answer a
    if (fields.answerA.trim().length < 1) {
      !valid;
      errors.answerA = 'Answer A cannot be empty';
    } else {
      errors.answerA = '';
    }
    // validate answer b
    if (fields.answerB.trim().length < 1) {
      !valid;
      errors.answerB = 'Answer B cannot be empty';
    } else {
      errors.answerB = '';
    }

    // add new poll
    if (valid) {
      let poll = {
        ...fields,
        votesA: 0,
        votesB: 0,
        id: Math.random() * (1 + Math.random()),
      };
      PollStore.update((currentPolls) => [poll, ...currentPolls]);
      dispatch('add');
    }
  };
</script>

<form on:submit|preventDefault={submitHandler}>
  <div class="form-field">
    <label for="question">Poll Question:</label>
    <input type="text" id="question" bind:value={fields.question} />
    <div class="error">{errors.question}</div>
  </div>
  <div class="form-field">
    <label for="answer-a">Answer A:</label>
    <input type="text" id="answer-a" bind:value={fields.answerA} />
    <div class="error">{errors.answerA}</div>
  </div>
  <div class="form-field">
    <label for="answer-b">Answer B:</label>
    <input type="text" id="answer-b" bind:value={fields.answerB} />
    <div class="error">{errors.answerB}</div>
  </div>
  <Button type="secondary" flat={true}>Add Poll</Button>
</form>

<style>
  form {
    width: 400px;
    margin: 0 auto;
    text-align: center;
  }

  .form-field {
    margin: 1.2rem auto;
  }
  input {
    width: 100%;
    border-radius: 0.6rem;
  }
  label {
    margin: 0.8rem auto;
    text-align: left;
  }
  .error {
    font-weight: bold;
    font-size: 0.8rem;
    color: tomato;
  }
</style>
