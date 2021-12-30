<template>
  <div id="menu">
    <div id="a">L</div>
    <div id="serchbar">
      <input v-model="titleL" id="search" class="shadow" placeholder="Title" />
      <button v-on:click="onClickToSearch()" id="go" class="btn shadow">Search</button>
    </div>
  </div>

  <div id="results" class="container">
    <div v-for="i in countL" v-bind:key="i" class="isCard shadow">
        <img class="img" :src="`${animesthumb[i-1]}`" alt="Card image cap">
        <div class="card-text">{{ animestitle[i-1] }}</div>
        
    </div>
  </div>

</template>

<script>
//   import vue from "vue"
//   import Card from './Card.vue'
  import axios from 'axios'

  export default {
    name: 'Index',
    // components: {
    //     Card
    // },
    data: function() {
        return {
            titleL: '',
            thumbL: '',
            resultL: [],
            countL: 0,
            animestitle: [],
            animesthumb: [],
        }
    },
    methods: {
        onClickToSearch: async function() {
            try {
                    const res = (await axios.get("http://localhost:12345/api/"+this.titleL))
                    console.log(this.titleL)
                    console.log(res.data)
                    this.resultL = []
                    this.resultL = res.data
                    this.countL = 0
                    this.countL = this.resultL.count

                    this.animestitle = []
                    this.animesthumb = []

                    for (let i = 0; i < this.resultL.results.length; i++) {
                        this.animestitle.push(this.resultL.results[i].name)
                        this.animesthumb.push(this.resultL.results[i].img)
                    }

                    // console.log(this.thumbL)

                } catch (error) {
                    console.error(error)
                }
            }

            
        }
  }
</script>

<style>
  /* #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  } */

  #menu {
    /* position: relative; */
    margin-bottom: 200px;
    text-align: center;
  }
  
  #searchbar {
    display: flex;

  }

  #go {
    position: relative;
    width: 100px;
    height: 50px;
    background: rgb(241, 241, 241);
    font-size: 25px;
    border-radius: 5px;
    outline: none;
    color: #6e7b88;
    

  }

  #search {
      position: relative;
      /* left: 50%;
      transform: translateX(-50%); */
      width: 500px;
      height: 50px;
      background: rgb(241, 241, 241);
      border: none;
      font-size: 25px;
      /* float: left; */
      /* color: rgb(88, 88, 88); */
      border-radius: 5px;
      outline: none;
      color: #6e7b88;
      margin: 20px;
  }

  #results {
    /* position: relative; */
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    
  }
  
  .isCard {
    width: 250px;
    height: 400px;
    /* padding-left: 20px; padding-right: 20px; */
    margin: 30px;
  }

  .img {
    margin: 20px;
    width: 200px;
    height: 300px;
  }

</style>
