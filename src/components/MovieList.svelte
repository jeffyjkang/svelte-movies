<script lang='ts'>
  export let movies: {title: string, rating: number}[];
</script>

{#each movies as movie (movie.title)}
  <div>
    <h3>{movie.title}</h3>
    <p>Rating: {movie.rating}</p>
  </div>
{/each}

<style>
  div {
    text-align: left;
    padding-bottom: 8px;
    border-bottom: 1px dashed black;
  }
</style>

