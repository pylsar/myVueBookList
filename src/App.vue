<template>
  <div id="app">
    <Form @addBook="addBook" />
    <List
      :titleValue="titleValue"
      :authorValue="authorValue"
      :numberValue="numberValue"
      :bookList="bookList"
      @deleteBook="deleteBook"
    />
  </div>
</template> 

<script>
import Form from "./components/Form.vue";
import List from "./components/List.vue";
export default {
  name: "App",
  components: { 
    Form,
    List 
  },
  data() {
    return {
      bookList: [],
    };
  },
  methods: {
    addBook(titleValue, authorValue, numberValue) {
      this.bookList.push({
        titleValue: titleValue,
        authorValue: authorValue,
        numberValue: numberValue,
      });
      // this.bookList = JSON.parse(localStorage.getItem("bookList"));
    },
    deleteBook(index) {
      this.bookList.splice(index, 1);
    },
  },
  mounted() {
    // console.log("App mounted!");
    // if (localStorage.getItem("bookList")) {
    //   this.bookList = JSON.parse(localStorage.getItem("bookList"));
    // }
    if (localStorage.booklist) {
      this.booklist = JSON.parse(localStorage.booklist);
    }
  },
  watch: {
    // bookList: {
    //   handler() {
    //     console.log("BookList changed");
    //     localStorage.setItem("bookList", JSON.stringify(this.bookList));
    //   },
    // },
    //сохраняем данные
    booklist: {
      handler(newBook) {
        console.log(newBook);
        localStorage.booklist = JSON.stringify(newBook);
      },
    },
  },
};
</script>

<style style="scss">

</style>
