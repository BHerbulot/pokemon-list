<template>
    <div id="app">
        <!-- <poke-card 
            :pokeInfo="pokemonList[0]"
        ></poke-card> -->
        <div class="container">
            <poke-card 
                v-for="pokemon of pokemonList" 
                :key="pokemon.number"
                :pokeInfo="pokemon"
            >
            </poke-card>
        </div>
    </div>
</template>

<script>
import virtualList from 'vue-virtual-scroll-list';
import PokeCard from './components/pokemon-card.vue';
import { pokemons } from '../db.js';
export default {
    name: 'App',
    components: {
        virtualList,
        PokeCard,
    },
    data (){
        return {
            pokemonList: pokemons,
        };
    }
}
</script>

<style>
    html, body, #app{
        height: 100%;
    }
    body{
        padding: 20px;

    }
    .container{
        display: flex;
        flex-wrap: wrap;
    }
</style>
