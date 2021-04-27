/* eslint-disable vue/require-v-for-key */ /* eslint-disable
@typescript-eslint/no-explicit-any */
<template>
  <div id="nav" class="container">
    <div class="head">
      <h1>
        {{ Title }}
      </h1>
      <div id="locations">
        <Cinemas
          @movies-available="moviesAvailable"
          @showTime="show"
          location="Ilupeju"
          color="green"
        />
        <Cinemas
          @movies-available="moviesAvailable"
          @showTime="show"
          location="VI"
          color="blue"
        />
        <Cinemas
          @movies-available="moviesAvailable"
          @showTime="show"
          location="Ajah"
          color="orange"
        />
      </div>
    </div>
    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->
    <hr />
    <div class="movies">
      <h1>Movies :</h1>
      <p :key="movie.id" v-for="movie in movies">
        Title:
        <span>{{ movie.title }}</span>
      </p>
    </div>
  </div>
  <!-- <router-view /> -->
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cinemas from "./components/cinemas.vue";
// const mo = []
// import Movies from "./components/movies.vue";
export default defineComponent({
  name: "app",
  props: {
    Title: {
      type: String,
      default: "VAS CINEMA",
    },
  },
  components: {
    Cinemas,
    // Movies,
  },
  // eslint-disable-next-line @typescript-eslint/no-explicit-any
  data(): any {
    return {
      movies: [],
    };
  },
  methods: {
    // eslint-disable-next-line @typescript-eslint/no-explicit-any
    moviesAvailable(e: any) {
      console.log("main", e);
      this.movies = e;
    },
        // eslint-disable-next-line @typescript-eslint/no-explicit-any
    show(e: any){
      console.log('showtime',e)
    }
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
  padding-top: 50px;
  .container {
    border: 1px solid #2c3e50;
    .head {
      display: flex;
      justify-content: space-between;
      // align-items: flex-start;
    }
  }
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
