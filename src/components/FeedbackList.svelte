<script>
  import { fade, scale, fly } from 'svelte/transition';
  import { FeedbackStore } from '../stores';
  import FeedbackItem from './FeedbackItem.svelte';
</script>

{#each $FeedbackStore as fb (fb.id)}
  <div in:scale={{ duration: 300 }} out:fly={{ duration: 500, x: 800 }}>
    <FeedbackItem item={fb} />
  </div>
{/each}
