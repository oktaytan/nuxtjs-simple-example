<template>
  <nuxt-link :to="'jokes/' + id">
    <div class="joke">{{joke}}</div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Joke",
  props: ["joke", "id"]
};
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px solid #ccc;
  margin: 1rem 0;
  cursor: pointer;
}
</style>
