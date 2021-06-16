<template>
  <div class="header_container">
      <div class="header_logo">
          <img src="https://fontmeme.com/temporary/90d7ad0ac76991693a78931d3b0b6161.png" alt="logo">
      </div>
      <div class="header_right">
          <input
            placeholder="Cerca un film o serie tv"
            @keyup="$emit('searchedFilms', filmChoosed)"
            v-model.trim="filmChoosed" type="text" id="search"
          >

          <i 
          class="fas fa-search"
          @click="$emit('searchedFilms', filmChoosed)" 
          for="search"
          >
          </i>
          
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

    i {
        font-size: 25px;
        color: red;
        margin-left: 20px;
        margin-right: 10px;
        cursor: pointer;
    }

    input {
        border-radius: 20px;
        margin-top: 25px;
        margin-right: 10px;
        box-shadow: 2px 2px red;
    }
}

</style>