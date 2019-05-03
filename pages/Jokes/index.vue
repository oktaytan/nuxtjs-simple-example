<template>
  <div class="jokes__wrappper">
    <SearchJokes v-on:search-text="searchText"/>
    <div class="isloading" v-if="isLoading">Loading...</div>
    <Joke v-else v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";
import SearchJokes from "../../components/SearchJokes";

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: [],
      isLoading: true
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);
      this.jokes = res.data.results;
      this.isLoading = false;
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };
      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        );

        this.jokes = res.data.results;
      } catch (err) {
        console.log(err);
      }
    }
  },
  head() {
    return {
      title: "Dad jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for corny dad jokes"
        }
      ]
    };
  }
};
</script>

<style>
.jokes__wrappper {
  height: 100vh;
}

.isloading {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background-color: transparent;
  border: 15px solid #bbbbbb;
  margin: 100px auto;
  position: relative;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.2rem;
  color: #3584ce;
}

.isloading::after {
  content: "";
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background-color: transparent;
  border: 15px solid #3584ce;
  border-right-color: transparent;
  border-top-color: transparent;
  border-right-width: -15px;
  border-top-width: -15px;
  position: absolute;
  top: -15px;
  left: -15px;
  box-sizing: border-box;
  animation: rotate 1s linear infinite forwards;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
