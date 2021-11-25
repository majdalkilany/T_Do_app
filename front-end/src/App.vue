<template>
  <div class="container">
    <h1>
      To do app
    </h1>
  </div>
  <Form @creatTask="onUpdaite"></Form>
  <Cards v-bind:apiData="apiData"  @allData="onUpdaite">  </Cards>
 
</template>

<script>
import axios from "axios";
  
import Form from "./components/Form.vue";
import Cards from "./components/Cards.vue";

export default {
  name: "App",
  data() {
  return {
  apiData:[],
  evenCheck:false
}},

  components: {
    Form,
    Cards,
  },
  created() {
    this.getTasks()
  },
  methods: {
    getTasks: function () {
      axios
        .get("http://localhost:3030/")
        .then((res) => {
          this.apiData = res.data;
          // console.log(this.apiData)
        })
        .catch((error) => {
          console.log(error);
        });
    },
    onUpdaite : function (allData){
        console.log(allData, 'appppp')
        this.getTasks()
    }
  },
};
</script>

<style >

</style>
