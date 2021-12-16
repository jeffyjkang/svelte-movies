<script lang='ts'>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  let searchTerm: string = '';

  const search = (e: any) => {
    searchTerm = e.target.value;
    if (searchTerm) {
      dispatch('searchMovies', {searchTerm});
    } else {
      dispatch('clearSearch', {});
    }
  }
</script>

<input
  placeholder='Search Movies'
  bind:value={searchTerm}
  on:keyup={search}    
/>


<style>
  input {
    width: 80%;
    float: left;
  }
</style>

