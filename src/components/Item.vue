<template functional>
  <!-- <div class="results">
      <h1>{{props.item.name}}</h1>
      <h2>status: {{props.item.status}}</h2>
    <img :src="props.item.image" alt />
    
  </div> -->
  <div class="results">
 <div class="flip-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <img :src="props.item.image" alt="picture" style="width:300px;height:300px;">
    </div>
    <div class="flip-card-back">
      <h1>{{props.item.name}}</h1> 
      <p>status:  <strong> {{props.item.status}}</strong> </p> 
      <p>species: <strong>{{props.item.species}}</strong>  </p>
      <p>type: <strong>{{props.item.type}}</strong> </p>
      <p>origin location: <strong>{{props.item.origin.name}}</strong> </p>
    </div>
  </div>
</div>

  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>

.results {
    font-size: 0.9rem;
  margin-top: 10px;
  margin-bottom: 50px;
  object-fit: fill;
  display: flex;
  flex-direction: column;
  box-shadow: 0 23px 32px black;
  &:hover {
      cursor: pointer;
  }
  img {
    margin: auto;

  }
  p {
      margin: 5px auto;
  }
  
}


//flippin cards
.flip-card {
  width: 300px;
  height: 300px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
  cursor: pointer;
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  color: black;
}

.flip-card-back {
  background-color: #02aa42;
  color: white;
  transform: rotateY(180deg);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
 
}

</style>