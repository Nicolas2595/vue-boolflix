<template>
  <div class="movies_container">
      <ul>
            <li>{{ titolo }}</li>
            <li>
            {{ titoloOriginale  }}</li>
            <img v-if="lingua == 'it'" src="../assets/images/it.png" alt="language" />
            <img v-else-if="lingua == 'en'" src="../assets//images/en.png" alt="language">
            <li>{{ voto }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: "Movies",
    props:  {
    titolo: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
    }
};
</script>

<style lang="scss" scoped>
    .movies_container {
        width: calc(100% / 4 - 2rem);
        margin: 1rem;
        // L'height fissa è per debug anche il background
        height: 200px;
        background-color: chartreuse;

        img {
            width: 30px;
        }
    }
    
</style>