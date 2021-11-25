<template>
  <div class="container">
    <h3>{{ card.title }}</h3>
    <p>{{ card.description }}</p>

    <input type="button" value="delete"  class="btn" v-on:click="deleteTask(card._id)"  />
<button v-on:click="isHidden = !isHidden"   class="btn">update</button >


  </div>

<UpdateForm v-bind:isHidden="isHidden" v-bind:card="card"  @allData="onUpdaite" ></UpdateForm>
        
        



</template>






<script>
import axios from "axios";
import UpdateForm from "./UptadeForm.vue";
export default {
  name: "Card",
  data() {
      return {
          isHidden: true
          
          }
  },
  props: {
    card: Object,
  },
  methods: {
    deleteTask: function (id) {
      console.log(id);
      axios
        .delete(`http://localhost:3030/delete/${id}`)
        .then((res) => {
          this.apiData = res.data;
          // console.log(this.apiData)
         this.onUpdaite()
        })
        .catch((error) => {
          console.log(error);
        });
    },
    hideForm : function (isHid) {
        console.log(isHid)
    },
    onUpdaite : function (allData){
        this.$emit('allData', allData)
    }
  },
  components: {
      UpdateForm, 
  }
};
</script>



<style >

.container {
    background-color : #E7E9EB;
    height:50h ;
    width: 50vw;

}
.btn {
  background-color: #3a281a;
  border: none;
  color: white;
  padding: 5px 7px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}

</style>