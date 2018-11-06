<template>
  <div class="home">
    <header>
      <HelloWorld msg="T-shirts Challenge"/>
    </header>
    <aside>
      <Filtre></Filtre>
    </aside>
    <main>
      <!-- <Products></Products> -->
      <div class="card" v-for="(val, prop) in produits" :key="prop" v-if="val.prix <= limit"> 
        <span>{{val.name}}</span>
        <img :src="val.url" :key="prop"/>
        <span>{{val.prix}}€</span>
      </div>
    </main>
    <footer>
      <p>By Aminata SY</p>
    </footer>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
// import Products from '@/components/Products.vue'
import Filtre from '@/components/Filtre.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    // Products,
    Filtre
  },
       data() {
        return {
            search: [], 
            color: [],
            marque: [],
            limit: 40,
            produits: [
                {name:"college skull", marque:"puma", color:"white", url: require("../assets/puma2.jpg"), prix: "20"}, 
                {name:"harold hunter", marque:"fila", color:"red", url: require("../assets/fila1.jpg"), prix: "32"}, 
                {name:"consume", marque:"fila", color:"white", url: require("../assets/fila2.jpg"), prix: "20"}, 
                {name:"skateboard lover", marque:"puma", color:"black",url: require("../assets/puma.jpg"), prix: "10"}, 
                {name:"cbgb skull", marque:"obey", color:"white", url: require("../assets/obey.jpg"), prix: "20"},
                {name:"chemical", marque:"lacoste",  color:"black", url: require("../assets/lacoste.jpg"), prix: "35"},
                {name:"Super Boo", marque:"puma", color:"black", url: require("../assets/puma3.jpg"), prix: "40"},
                {name:"classic green", marque:"vans", color:"blue",url: require("../assets/vans.jpg"), prix: "29"},
                {name:"Motor maniacs", marque:"vans", color:"violet", url: require("../assets/vans2.jpg"), prix: "33"},
            ],
        }
    },

    created(){
      this.$ebus.$on("ranger", payload => {
          this.limit = payload
          console.log(this.limit);
      });
       this.$ebus.$on("colori", payload => {
          this.produits = this.produits.filter((val) => {
          return val.color.match(payload)
          console.log(payload)
      });
      console.log(this.color)
      });
       this.$ebus.$on("brand", payload => {
          this.produits = this.produits.filter((val) => {
          return val.marque.match(payload)
          console.log(payload)
      });
    });
}
}
</script>

<style lang="scss">
  header{
    position: fixed;
    width: 100%;
    height: 12%;
    top: 0;
    left: 0;
    background: rgb(228, 224, 224)
  }
  aside{
    float: left;
    border: 1px solid black;
    width: 28%;
    margin-top: 10%;
    margin-left: 7%
  }
  main{
    float: right;
    width: 50%;
    height: auto;
    margin-top: 10%;
    margin-right: 10%
  }
  footer{
    width: 100%;
    height: 10%;
    position: absolute;
    bottom: -290px;
  }
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

