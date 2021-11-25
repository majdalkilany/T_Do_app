<template>
  <div>
    <form v-if="!isHidden" form v-on:submit.prevent="updateCard">
      <input
        type="text"
        name="title"
        placeholder="title "
        v-model="form.title"
      />
      <input
        type="text"
        name="description"
        placeholder="description"
        v-model="form.description"
      />
      <input
        type="hidden"
        name="id"
        placeholder="description"
        v-model="form._id"
      />

      <input
        type="submit"
        name="submit"
        value="submit"
        v-on:click="updateCard(),senDataBacked()"
        
      />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      isHidde: false,
      form: {
        title: this.card.title,
        description: this.card.description,
        _id: this.card._id,
      },
      allData:[]
    };
  },
  methods: {
    updateCard: function () {
      console.log(this.form);
      axios
        .put(`http://localhost:3030/update/${this.form._id}`,this.form)
        .then((res) => {
          this.allData = res.data
        //   console.log(this.allData ,'alll ')
        });
    },
    senDataBacked: function () {
this.$emit('allData',this.allData)
    }
  },
  props: ["isHidden", "card"],
};
</script>
