<template>
  <button @click="onClick(location)" class="btn" :style="{ background: color }">
    {{ location }}
  </button>
  <!-- <button>VI</button>
  <button>Ajah</button> -->
</template>

<script>
// import { defineComponent } from '@vue/composition-api'
import Movies from "../movies/movies";
import showTime from "../movies/showTime";
export default {
  name: "Cinemas",
  props: {
    location: String,
    color: String,
  },
  methods: {
    onClick(e) {
      this.$emit("movies-available", Movies);
      let res = showTime.filter((item) => {
        console.log("res one",item.id );
        return item.id == e;
      }, console.log('eee',res));
    },
  },
};
</script>

<style scoped></style>
