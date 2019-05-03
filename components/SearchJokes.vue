<template>
  <form class="search__form" @submit.prevent="onSubmit">
    <input class="form__input" type="text" v-model="text" placeholder="Search Jokes...">
    <input class="form__btn" type="submit" value="Search Jokes">
  </form>
</template>

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>

<style >
.search__form {
  display: flex;
  width: 100%;
  justify-content: center;
  margin: 30px 0;
}

.form__input {
  width: 50%;
  height: 2.3rem;
  padding: 0 1rem;
  font-size: 1.2rem;
  outline: none;
  border: 1px solid #318abd;
  line-height: 2.3rem;
}
.form__btn {
  height: 2.3rem;
  padding: 0 1rem;
  font-size: 1rem;
  outline: none;
  border: 1px solid #318abd;
  background-color: #318abd;
  color: #fff;
  line-height: 2.3rem;
  cursor: pointer;
  transition: all 0.25s ease;
}

.form__btn:hover {
  background-color: #236286;
  border: 1px solid #236286;
}
</style>
