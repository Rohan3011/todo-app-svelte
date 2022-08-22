<script>
  export let count;
  export let average;
</script>

<div class="feedback-stats">
  <p>{count} Reviews</p>
  <p>Average rating: {average}</p>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 8px;
  }
</style>
