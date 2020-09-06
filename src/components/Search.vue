<template>
  <div class="searchBar">
    <p>a rick and morty world search app</p>
    <div class="tab">
      <input 
      type="text" 
      :value="value" 
      class="searchBar__input" 
      placeholder="search..." 
      @input="handleInput"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
    };
  },
  props: {
    value: "",
  },
  methods: {
    handleInput(e) {
      console.log("dupa");
      this.$emit("input", e.target.value)
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.searchBar {
  display: flex;
  flex-direction: column;
  position: relative;
  align-self: center;
  margin-bottom:100px;
    p {
    color: white;
    margin: auto;
        background-color: rgba(0, 0, 0, 0.658)  ;
        padding: 5px;
        margin-bottom: 25px;
        font-weight: 400;

  }

}
.tab {
  display: flex;
  margin: auto;
  border-radius: 100%;
  height: 50px;
  input {
    font-size: 1.5rem;
    border:none;
    background-color: rgba(0, 0, 0, 0.658)  ;
    border-bottom: 2px solid white;
    color:white;
    text-align: center;
    border-radius: 0%;
    transition: box-shadow ease-in 0.2s, border-radius 0.2s ease-in, border-bottom 0.2s ease-in, background-color 0.2s ease-in
    ;
     &:focus {
    box-shadow: 0 0 29px 50px rgb(3, 255, 37);
    border-radius: 50%;
    border-bottom: 2px solid rgb(3, 255, 37);
    background-color: rgba(1, 51, 8, 0.822);
  }
  }
}
</style>
