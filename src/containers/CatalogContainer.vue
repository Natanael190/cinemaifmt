<template>
  <div class="catalog-container">
    <div class="container">      
      <div class="content">
        <div v-if="currentMovie" class="movie-content">
          <img class="movie-poster" :src="currentMovie.posterUrl" :alt="currentMovie.title" />
          <div class="movie-details">
            <h2>{{ currentMovie.title }}</h2>
            <h4>{{ currentMovie.year }}<span v-if="currentMovie.runtime"> - {{ currentMovie.runtime }}mins</span></h4>
            <p v-if="currentMovie.plot">{{ currentMovie.plot }}</p>
            <p v-if="currentMovie.director"><strong>Director:</strong> {{ currentMovie.director }}</p>
            <p v-if="currentMovie.plot"><strong>Actors:</strong>{{ currentMovie.actors }}</p>
            <p v-if="currentMovie.genres"><strong>Tags:</strong> {{ currentMovie.genres.join(" / ") }}</p>
          </div>
        </div>
        <div class="sidebar">
          <List v-if="movies && movies.length > 0" :active="currentMovie.id" :items="movies" @movie-selection="handleMovieSelection" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import './containers.scss';
  import data from '../data/movies.json';
  import List from '../components/list/List.vue'
  export default {
    name: "CatalogContainer",
    components: {
      List,
    },
    data() {
      return {
        movies: [],
        currentMovie: null
      }
    },
    mounted() {
      this.movies = data.movies;
      if(this.movies.length > 0) {
        this.currentMovie = this.movies[0];
      }
    },
    methods: {
      handleMovieSelection(movie) {
        this.currentMovie = movie;
      }
    }
  };
</script>
