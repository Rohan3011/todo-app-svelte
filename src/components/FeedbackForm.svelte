<script>
  import { v4 as uuidv4 } from "uuid";
  import { createEventDispatcher } from "svelte";

  const MIN_CHAR = 10;
  let text = "";
  let btnDisabled = true;
  let message = "";
  let selected = 5;

  const dispatch = createEventDispatcher();

  const handleSelect = (e) => {
    selected = e.currentTarget.value;
  };

  const handleInput = () => {
    if (text.trim().length < MIN_CHAR) {
      message = `Review must be aleast ${MIN_CHAR} long`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  const handleSubmit = () => {
    const newFeedback = {
      id: uuidv4(),
      text: text,
      rating: selected,
    };
    dispatch("add-feedback", newFeedback);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <h3>How would you like to rate our service?</h3>

  <!-- rating selector -->
  <div class="rating-menu">
    <select value={selected} on:change={handleSelect} name="Rating" id="">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
  </div>

  <div class="input-group">
    <input
      type="text"
      on:input={handleInput}
      bind:value={text}
      placeholder="How can we improve?"
    />
  </div>

  {#if message}
    <div class="message">
      <p>{message}</p>
    </div>
  {/if}

  <button disabled={btnDisabled} type="submit">send</button>
</form>

<style>
  button:disabled {
    pointer-events: none;
  }

  .message {
    padding: 4px;
    color: aliceblue;
  }
</style>
