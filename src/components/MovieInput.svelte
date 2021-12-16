<script lang='ts'>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  let title: string = '';
  let rating: number = 1;

  const submitMovie = () => {
    if (title) {
      dispatch('submitMovie', {
        title,
        rating
      });
    }
    title = '';
    rating = 1;
  }
</script>

<div class='input-container'>
  <input
    placeholder='Movie Title'
    type='text'
    bind:value={title}
  />
  <select bind:value={rating}>
    {#each [1,2,3,4,5] as val}
      <option value={val}>{val}</option>
    {/each}
  </select>
  <button
    disabled={!title}
    on:click|preventDefault={submitMovie}
  >
    Submit
  </button>
</div>

<style>
  .input-container {
    width: 100%;
    display: flex;
  }
  .input-container input {
    flex: 1;
  }
  .input-container select {
    width: 80px;
    margin-right: 8px;
    margin-left: 8px;
  }
  .input-container button {
    width: 80px;
  }
</style>

