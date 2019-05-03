<template>
  <header class="header">
    <h1 class="title">Dad jokes</h1>
    <ul>
      <li>
        <nuxt-link to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/jokes">Jokes</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/about">About</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "AppHeader"
};
</script>

<style>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px dotted #ccc;
}
.header .title {
  font-size: 3rem;
  color: #318abd;
}
.header ul {
  display: flex;
}
.header a {
  display: inline-block;
  background: #318abd;
  color: #fff;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
  transition: all 0.25s ease;
}

.header a:hover {
  background-color: #236286;
}
</style>
