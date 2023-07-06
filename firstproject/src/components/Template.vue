<style>
.box{
  padding: 100px 0;
  width:400px ;
  text-align: center;
  background: rgb(182, 181, 181);
  margin: 20px;
  display: inline-block;

}
li{
  list-style: none;
  background: rgb(211, 205, 205);
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
<template>
    <div class="FeatureTemplate">
      <div v-if="showNum">
          <ul>
            <li v-for="movie in movies" :key="movie.title" :class="{fav : movie.isFav}">
              <img :src="movie.img"/>
              
              <h3>{{movie.title}}</h3>
              {{movie.hero}}
            </li>
          </ul>
      </div>
        
        <button @click="incrementNum">Increase</button>
        <button @click="decreaseNum">Decrease</button>
        <button @click="HideNum">Toggle</button>



        <br>
        <div class="box" @mouseover="eventHandler($event)">Hover</div>
        <div class="box" @mouseleave="eventHandler">Mouse Leave</div>
        <div class="box" @dblclick="eventHandler">Double Click</div>
        <div class="box" @mousemove="mouseMoveEvent">position - {{x}} {{y}}</div>
    </div>
</template>
<script>
export default {
  name: 'FeatureTemplate',
  props:{
    num:{
      type:Number,
      required:true,
    }
  },
  data() {
    return {
      localNum: this.num,
      showNum:true,
      x:0,
      y:0,
      movies:[
        {title:"Loot",hero:"Dayahang",img:"../assets/loot.jpg" , isFav:true},
        {title:"Bhaire",hero:"Tori Laure",img:"../assets/bhaire.jpg",isFav:false},
        {title:"Family Guy",hero:"Peter",img:"../assets/fguy.jpg",isFav:true}
      ]
    };
  },
  methods: {
    incrementNum() {
      this.localNum++; // Update the local data property
      this.$emit('update:num', this.localNum); // Emit an event to notify the parent component
    },
    decreaseNum(){
      this.localNum--;
      this.$emit('update:num',this.localNum);
    },
    HideNum(){
      this.showNum=!this.showNum;
    },
    eventHandler(e){
        console.log(e,e.type);
    },
    mouseMoveEvent(e){
      this.x=e.offsetX;
      this.y=e.offsetY;
    }

  }
}
</script>