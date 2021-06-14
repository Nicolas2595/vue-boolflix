<template>
  <div class="header_container">
      <div class="header_logo">
          <img src="https://fontmeme.com/temporary/90d7ad0ac76991693a78931d3b0b6161.png" alt="">
      </div>
      <div class="header_right">
          <input
          placeholder="Cerca un film o serie tv"
          @keyup="$emit('searchedFilms', filmChoosed)"
           v-model.trim="filmChoosed" type="text" id="search"
          >

          <button
          @click="$emit('searchedFilms', filmChoosed)"  for="search">Search</button
          >
          
      </div>
  </div>
</template>

<script>
export default {
    name: "Header",
    data: function() {
        return {
            filmChoosed: ''
        }
    }
    
}
</script>

<style lang="scss" scoped>

.header_container {
    display: flex;
    justify-content: space-between;
    background-color: black;
}

.header_logo img {
    height: 50px;
    margin-top: 20px;
    cursor: pointer;
    
}

.header_right {
     
    height: 80px;

    button {
        height: 25px;
        margin-top: 25px;
        margin-right: 10px;
    }

    input {
        border-radius: 20px;
        margin-top: 25px;
        margin-right: 10px;
    }
}

</style>