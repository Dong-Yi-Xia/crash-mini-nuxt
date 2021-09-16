<template>
  <header class="header">
    <h1 class="title">Dad Jokes</h1>
    <ul>
      <!-- don't use the <a> tag use the nuxk-link with to path -->
      <!-- inside the pages folder, the route /path will the the folder name having index.vue or with a folder just filename.vue -->
      <li>
        <nuxt-link to="/">Home</nuxt-link>
        <nuxt-link to="/jokes">Jokes</nuxt-link>
        <nuxt-link to="/about">About</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name:'AppHeader', //when its a component it needs a name

}
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
  color: #526488;
}
.header ul {
  display: flex;
}
.header a {
  display: inline-block;
  background: #333;
  color: #fff;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
}
</style>
