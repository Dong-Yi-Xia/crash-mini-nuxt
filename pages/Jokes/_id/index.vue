<template>
  <!-- having localhost:3000/jokes/id need to create a folder inside parent folder with a underscore in front, _id -->
  <div>
      {{$route.params.id}}
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
