<script>
  import FeedbackForm from './components/FeedbackForm.svelte';
  import FeedbackList from './components/FeedbackList.svelte';
  import FeedbackStats from './components/FeedbackStats.svelte';
</script>

<main class="container">
  <h1 class="container__main__title">
    Feedback Reviews page using
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img
      class="container__main__image"
      src="images/svelte-logo.svg"
      alt="svelte image"
    />
  </h1>

  <FeedbackForm />
  <FeedbackStats />
  <FeedbackList />
</main>
