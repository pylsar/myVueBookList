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
        <button class="btn__remove" @click="deleteBook(index)">delete</button>
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

<style lang="scss">
.table{
    width: 100%;
    & thead{
        & tr{
            & th{
                width: 25%;
                text-align: left;
                padding: 12px;
            }
        }
    }
    & tbody{
        & td{
            width: 25%;
            text-align: left;
            padding: 12px;
        }
    }
}
.btn__remove{
    outline: none;
    border: none;
    padding: 12px;
    background: rgb(247, 81, 4);
    cursor: pointer;
}
</style>

