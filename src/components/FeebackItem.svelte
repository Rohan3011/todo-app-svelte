<script>
  import { createEventDispatcher } from "svelte";

  export let item;

  const dispatch = createEventDispatcher();

  const handleDelete = (itemId) => {
    dispatch("delete-feedback", itemId);
  };
</script>

<main>
  <div class="card">
    <div class="rating">{item.rating}</div>
    <slot>{item.text}</slot>
    <button on:click={() => handleDelete(item.id)}>delete</button>
  </div>
</main>

<style>
  .card {
    background: #ff3c00;
    border-radius: 5px;
    padding: 10px;
    margin: 4px;
    margin-bottom: 8px;
    color: white;
    display: flex;
    flex-direction: column;
    row-gap: 5px;
  }

  .rating {
    width: 30px;
    height: 30px;
    display: grid;
    place-items: center;
    background-color: #1a1a1a;
    color: white;
    border-radius: 15px;
  }
</style>
