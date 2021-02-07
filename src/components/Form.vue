<template>
  <div>
    <form class="form" @submit.prevent="addBook">
      <div>
        <label for="title">Title</label>
        <input type="text" id="title" v-model="titleValue" required>
      </div>
      <div>
        <label for="author">Author</label>
        <input type="text" id="author" v-model="authorValue" required>
      </div>
      <div>
        <label for="numValue">Number</label>
        <input type="number" id="numValue" v-model="numberValue" required>
      </div>
      <button type="submit" :disabled="numberValue <=0">Add Book</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "Form",
  data() {
    return {
      titleValue: "",
      authorValue: "",
      numberValue: ""
    };
  },
  methods: {
    addBook() {
      this.$emit("addBook", this.titleValue, this.authorValue, this.numberValue);
      this.titleValue = "";
      this.authorValue = "";
      this.numberValue = "";
    }
  }
};
</script>
<style>
</style>


