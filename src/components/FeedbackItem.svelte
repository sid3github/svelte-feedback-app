<script>
  import { FeedbackStore } from '../stores';
  import Card from './Card.svelte';
  export let item;

  const deleteCard = (itemId) => {
    FeedbackStore.update((currentFeedback) => {
      return currentFeedback.filter((item) => item.id !== itemId);
    });
  };
</script>

<Card>
  <div class="num-display">
    {item.rating}
  </div>
  <button on:click={deleteCard(item.id)} class="close"> ❌ </button>
  <p class="text-display">
    {item.text}
  </p>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: royalblue;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>
