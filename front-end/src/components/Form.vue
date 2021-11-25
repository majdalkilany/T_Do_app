<template>
  <div>
    <form form v-on:submit.prevent="onIput">
      <input
        type="text"
        name="title"
        placeholder="title "
        v-model="form.title"
      />
      <br />
      <br />
      <input
        type="text"
        name="description"
        placeholder="description"
        v-model="form.description"
      />

      <input
        type="submit"
        name="submit"
        value="submit"
        v-on:submit.prevent="onIput"
      />
    </form>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import axios from "axios";

export default {
  name: "Form",
  data() {
    return {
      form: {
        title: "",
        description: "",
      },
    };
  },

  methods: {
    onIput: function () {

console.log(this.form)
axios.post('http://localhost:3030/create/', this.form)
                 .then((res) => {
                   this.$emit('creatTask')
                   console.log(res)
                 })
                 .catch((error) => {
                   console.log(error)
                 })
},

  },
};
</script>

<style>
input[type=text] {
  width: 20%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}
</style>