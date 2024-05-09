<script>
  import { v4 as uuid4 } from 'uuid';
  import { FeedbackStore } from '../stores';
  import Card from './Card.svelte';
  import Button from './Button.svelte';
  import RatingSelect from './RatingSelect.svelte';

  let text = '';
  let btnDisabled = true;
  let min = 10;
  let message;
  let rating = 10;

  const handleSubmit = () => {
    if (text.trim().length > min) {
      const newFeedback = {
        id: uuid4(),
        text: text,
        rating: +rating,
      };
      FeedbackStore.update((currentFeedback) => [
        newFeedback,
        ...currentFeedback,
      ]);
      text = '';
    }
  };

  const handleSelect = (e) => (rating = e.detail);

  const handleInput = () => {
    if (text.trim().length <= min) {
      btnDisabled = true;
      message = `Text must be atleast ${min} characters`;
    } else {
      btnDisabled = false;
      message = null;
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate your service with us ?</h2>
  </header>
  <RatingSelect on:rating-select={handleSelect} />
  <form on:submit|preventDefault={handleSubmit}>
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        on:input={handleInput}
        placeholder="Tell us something that keeps you coming back"
      />
      <Button type="submit" disabled={btnDisabled}>Send</Button>
    </div>
    {#if message}
      <div class="message">{message}</div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
