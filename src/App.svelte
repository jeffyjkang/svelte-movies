<script lang="ts">
  import MovieInput from './components/MovieInput.svelte';
  import MovieList from './components/MovieList.svelte';
  import MovieSearch from './components/MovieSearch.svelte';

  let movies = localStorage.getItem('movies') ?
    JSON.parse(localStorage.getItem('movies')) :
    [];

  const addMovie = (movie: {title: string, rating: number}) => {
    const updatedMovies = [movie, ...movies];
    localStorage.setItem('movies', JSON.stringify(updatedMovies));
    movies = updatedMovies;
  }

  const resetMovies = () => {
   movies = localStorage.getItem('movies') ?
    JSON.parse(localStorage.getItem('movies')) :
    []; 
  }
  const filterMovies = (searchTerm: string) => {
    const tempMovies = localStorage.getItem('movies') ?
      JSON.parse(localStorage.getItem('movies')) :
      []; 
    movies = tempMovies.filter(
      (m: {title: string, rating: number}) => m.title.toLowerCase()
        .includes(searchTerm.toLowerCase())
      )
  }
</script>

<div class='main'>
  <h1 class='header'>
    Movie Journal
  </h1>
  <MovieSearch
    on:clearSearch={resetMovies}
    on:searchMovies={
      (event) => filterMovies(event.detail.searchTerm)
    }
  />
  <MovieInput
    on:submitMovie={
      (event) => addMovie(event.detail)
    } 
  />
  <MovieList movies={movies}/>
</div>

<style>
  .main {
    max-width: 800px;
    padding: 1rem;
    margin: auto;
    text-align: center;
  }
  .header {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
</style>

