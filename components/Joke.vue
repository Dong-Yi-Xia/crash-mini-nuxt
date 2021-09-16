<template>
  <nuxt-link :to="`/jokes/${id}`">
    <div class="joke">
      <p>{{ joke }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'Joke',
  props: {
    joke: String,
    id: String
  }
}
</script>

<style>

</style>
