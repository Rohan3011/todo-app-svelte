<script>
  import FeedbackForm from "./components/FeedbackForm.svelte";

  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";

  // feedback : {id: string, text: string, rating: number}
  let feedback = [];

  $: count = feedback.length;
  $: average =
    feedback.reduce((prev, { rating }) => prev + rating, 0) / feedback.length ||
    0;

  const addFeedback = (e) => {
    const newFeedback = e.detail;
    feedback = [newFeedback, ...feedback];
  };

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id != itemId);
  };
</script>

<main>
  <FeedbackForm on:add-feedback={addFeedback} />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
