<template>
    <div class="movies_container">
        <img :src="img_url + poster">
        <div class="movies">
            <h6>Titolo: {{ titolo }} </h6>
            <h6>Titolo Originale: 
            {{ titoloOriginale  }} </h6>
            <img class="lingua" 
            v-if="lingua == 'it'" src="../assets/images/it.png" alt="language" />
            <img class="lingua" 
            v-else-if="lingua == 'en'" src="../assets//images/en.png" alt="language">
            <div class="star">
                <h5>Voto:</h5> 
                <span>
                    <i v-for="i in 5" :key="i" :class="i <= changeVoto ? 'fas fa-star' : 'far fa-star'"></i>
                </span>
            </div>
            <p>Overview: {{ overview }} </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Movies",
    props:  {
    poster: String,
    titolo: String,
    overview: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
    },
    data() {
        return {
            img_url: "https://image.tmdb.org/t/p/w342", 
        }
    },
    computed: {
        changeVoto() {
            return Math.round(parseInt(this.voto) / 2);
        }
    }
};
</script>

<style lang="scss" scoped>
    .movies_container {

        width: calc(100% / 4);
        margin: 1rem;
        height: 350px;
        width: 200px;
        position: relative;

         img {
            height: 100%;
            width: 100%;
            border-radius: 10px;
        }

        .movies {
            text-align: center;
            background-color: rgba(0, 0, 0, 0.8);
            width: 200px;
            height: 350px;
            position: absolute;
            cursor: pointer;
            top: 0;
            visibility: hidden;
            overflow: auto;
            border-radius: 10px;
            padding: 10px;

            h5 {
                color: lightgrey;
                font-size: 13px;
            }

            h6 {
                color: lightgrey;
                font-size: 13px;
            }

            p {
                color: lightgrey;
                font-size: 12px;
                padding-top: 20px;
            }

            .star {
                
                i {
                    color: yellow;
                }
            }

            .lingua {
                width: 30px;
                height: 30px;
                padding-bottom: 10px;
            }
        }
    }

    .movies_container:hover .movies {
        visibility: visible;
    }
    
</style>