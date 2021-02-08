<template>
  <div id="app">
    <Theme/>
    <h1>Храните книги в порядке</h1>
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
import Theme from "./components/Theme.vue";
import Form from "./components/Form.vue";
import List from "./components/List.vue";
export default {
  name: "App",
  components: { 
    Theme,
    Form,
    List 
  },
  data() {
    return {
      bookList: [],
      titleValue: "",
      authorValue: "",
      numberValue: ""
    };
  },
  methods: {
    addBook(titleValue, authorValue, numberValue) {
      this.bookList.push({
        titleValue: titleValue,
        authorValue: authorValue,
        numberValue: numberValue,
      });
    },
    deleteBook(index) {
      this.bookList.splice(index, 1);
    },
  },
  mounted() {
    if (localStorage.getItem("bookList")) {
      this.bookList = JSON.parse(localStorage.getItem("bookList"));
    }
    if (localStorage.booklist) {
      this.booklist = JSON.parse(localStorage.booklist);
    }
  },
  watch: {
    bookList: {
      handler() {
        // console.log("BookList changed");
        localStorage.setItem("bookList", JSON.stringify(this.bookList));
      },
    },
  },
};
</script>

<style style="scss">
*{
  margin: 0;
  padding: 0;
}
#app{
  width: 80vw;
  height: 100vh;
  margin: 0 auto;
}
h1{
  text-align: center;
  font-size: 5vw;
  padding-top: 50px;
  padding-bottom: 50px;
}


</style>
