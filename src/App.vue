<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <Search @input="handleInput" v-model="searchQuery" />
    <transition name="fade"> 
    <div class="res" v-if="step===1">
      <Item v-for="item in results" :item="item" :key="item.id" />
    </div>

    </transition>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./components/Search";
import Item from "./components/Item";
import debounce from "lodash.debounce";

const baseUrl = "https://rickandmortyapi.com/api/character/?name=";

export default {
  name: "App",
  components: {
    Search,
    Item,
  },
  data() {
    return {
      searchQuery: "",
      results: [],
      step: 0
    };
  },
  methods: {
    handleInput: debounce(function () {
      const query = baseUrl + this.searchQuery;
      console.log(query);
      if (this.searchQuery) {
        axios
          .get(query)
          .then((res) => {
            console.log(res.data);
            this.results = res.data.results;
            this.step=1
          })
          .catch((err) => console.log(err));
      } else {
        this.results = [];
      }
    }, 500),
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500&display=swap");

html,
* {
  // background: linear-gradient(rgba(0, 0, 255, 0.178), dodgerblue);
  // background-repeat: no-repeat;
  // background-size: contain;
  // background-position: center;
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  box-sizing: border-box;
}
#app {
  min-height: 100vh;
  display:flex;
  flex-direction: column;
  
  background-image: url("https://images.pexels.com/photos/1585325/pexels-photo-1585325.jpeg?auto=compress&cs=tinysrgb&dpr=3&h=750&w=1260");
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
  
}

.res {
  // border: 2px solid black;
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
  justify-content: center;
  font-size: 0.6rem;
  
}


.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

