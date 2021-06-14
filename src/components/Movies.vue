<template>
  <div class="movies_container">
      <ul>
            <li>{{ item.title }}</li>
            <li>{{ item.original_title }}</li>
            <img v-if="item.original_language == 'it'" src="../assets/images/it.png" alt="language" />
            <img v-else-if="item.original_language == 'en'" src="../assets//images/en.png" alt="language">
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
    .movies_container {
        width: calc(100% / 4 - 2rem);
        margin: 1rem;

        img {
            width: 30px;
        }

    }
    
</style>