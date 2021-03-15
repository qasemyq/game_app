<template>
  <div>
      <div id="vue-app">

        <div id="boxing-bag" v-bind:class="{bag_destroy: ended}"></div>

        <div id="health">
          <div v-bind:style="{width: health + '%'}"></div>
        </div>

        <div id="controls">
          <button v-on:click="punch" v-show="!ended">Punch</button>
          <button v-on:click="restart">Restart</button>
        </div>
      </div>
  </div>
    
</template>

<script>
export default {
  data(){
    return{
      health: 100,
      ended: false
    }
  },
  methods:{
    punch(){
      this.health -= 10
      if(this.health <= 0){
        this.ended = true
      }
    },
    restart(){
      this.health = 100
      this.ended = false
    }
  }
}
</script>

<style scoped>

#boxing-bag{
  width: 400px;
  height: 500px;
  margin: 0 auto;
   background: url('../assets/punch.png') center no-repeat;
}

#health{
  width: 400px;
  border: 2px solid #000;
  margin: 0 auto 20px auto;
}

#health div{
  height:20px;
  background: crimson;
}

#controls{
  width: 120px;
  margin: 0 auto;
}

button{
  width: 110px;
  height: 30px;
  margin-top: 4px;
  background-color: black;
  color: aliceblue;
  font-size: 20px;
  border: none;

}

button:hover{
  background-color: red;
}

#boxing-bag.bag_destroy{
   background: url('../assets/bag-burst.png') center no-repeat;
}
</style>
