<template>
  <table class="table">
    <thead>
      <tr>
        <th>Title</th>
        <th>Auther</th>
        <th>Rating</th>
        <th></th>
      </tr>
    </thead>
    <tbody class="book__list" v-for="(book, index) in bookList" :key="index">
      <td>{{book.titleValue}}</td>
      <td>{{book.authorValue}}</td>
      <td>{{book.numberValue}}</td>
      <td>
        <button @click="deleteBook(index)">delete</button>
      </td>
    </tbody>
  </table>
</template>
<script>
export default {
  name: "List",
  props: ["titleValue", "authorValue", "numberValue", "bookList"],
  methods: {
    deleteBook(index) {
      this.$emit("deleteBook", index);
    }
  },
};
</script>

