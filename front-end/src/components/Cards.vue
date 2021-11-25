<template>
  <div >
    <Card v-for="(card) in apiData" :key="card"
    v-bind:card="card"

    @allData="onUpdaite"
    ></Card>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
// import axios from "axios";
import Card from './Card.vue'

export default {
  name: "Cards",


  
  props :{
    apiData: Array,
  },
  methods: {
    onUpdaite : function (allData){
        console.log(allData, 'from cards')
        this.$emit('allData', allData)
    }
  },
  components: {
    Card
  }
};
</script>
