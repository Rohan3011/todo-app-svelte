<script>
  import FeebackItem from "./FeebackItem.svelte";

  export let feedback = [];
</script>

<main>
  {#if feedback.length}
    {#each feedback as fb (fb.id)}
      <FeebackItem item={fb} on:delete-feedback />
    {/each}
  {:else}
    <div><p>Add your first review!</p></div>
  {/if}
</main>
