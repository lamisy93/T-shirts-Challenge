<template>
  <div>
    <!-- <div class="card" v-for="(val, prop) in produits" :key="prop">{{val.name}} {{val.src}} {{val.prix}}€</div> -->
    
    <div class="card"  v-for="(val, prop) in produits" :key="prop" v-bind:class="filteredList">
      <span>{{val.name}}</span>
      <img :src="val.url" :key="prop"/>
      <span>{{val.prix}}€</span>
    </div>

  </div>
    
</template>

<script>
import Filtre from '@/components/Filtre.vue'
export default {

     components: {
     Filtre,
     },

        data() {
        return {
            produits: [
                {name:"college skull", marque:"puma", url: require("../assets/puma2.jpg"), prix: "20"}, 
                {name:"harold hunter", marque:"fila", url: require("../assets/fila1.jpg"), prix: "32"}, 
                {name:"consume", marque:"fila", url: require("../assets/fila2.jpg"), prix: "20"}, 
                {name:"skateboard lover", marque:"puma", url: require("../assets/puma.jpg"), prix: "10"}, 
                {name:"cbgb skull", marque:"obey", url: require("../assets/obey.jpg"), prix: "20"},
                {name:"chemical", marque:"lacoste", url: require("../assets/lacoste.jpg"), prix: "35"},
                {name:"Super Boo", marque:"puma", url: require("../assets/puma3.jpg"), prix: "40"},
                {name:"classic green", marque:"vans", url: require("../assets/vans.jpg"), prix: "29"},
                {name:"Motor maniacs", marque:"vans", url: require("../assets/vans2.jpg"), prix: "33"},
            ],
        }
    },
    methods: {
    test(evt) {
    this.$ebus.$emit("liaison", {done: true});
  }
}
    
}
</script>

<style scoped>
  
  div.card{
    border: 1px solid black;
    width: 200px;
    height: 200px;
    display: inline-block;
    margin: 5px;
    padding-top: 15px
  }

  img{
      width: 150px;
      height: 150px;
  }

</style>

