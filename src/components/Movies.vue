<template>
  <div class="movies_container">
      <ul>
          <li>{{ item.title }}</li>
          <li>{{ item.original_title }}</li>
          <li>{{ item.original_language }}</li>
          <li>{{ item.vote_average }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: "Movies",
    props: ['item']
}
</script>

<style lang="scss" scoped>


</style>