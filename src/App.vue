<template>
  <div id="app" class="app" :class="{ dark: checked }">
    <div class="container">
      <div class="theme">
        <div class="theme__box" :class="{ theme__dark: checked }">
            <label
            class="theme__label"
            for="theme"
            :class="{ theme__choose: checked }"
            >
            <input
                class="theme__toggle"
                id="theme"
                type="checkbox"
                v-model="checked"
            />
            </label>
        </div>
      </div>
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
      titleValue: "",
      authorValue: "",
      numberValue: "",
      checked: false
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
    changeTheme(){
      this.checked = !this.checked;
    }
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

<style lang="scss">
*{
  margin: 0;
  padding: 0;
}
.app{
  width: 100%;
  height: 100vh;
  background: white;
  color: black;
}
.container{
  width: 90%;
  margin: 0 auto;
}
h1{
  text-align: center;
  font-size: 5vw;
  padding-top: 50px;
  padding-bottom: 50px;
}

.theme {
  position: absolute;
  top: 5%;
  right: 15%;
  width: 48px;
  height: 26px;
  border: 2px solid black;
  border-radius: 20px;
  &__box{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 20px;
  }
  &__toggle{
    display: none;
  }
  &__label{
  content: "";
  display: block;
  background: black;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  }
  &__choose{
    left: 50%;
  }
  &__dark{
    background: gray;
  }
}

.dark{
  background: gray;
  color: white;
}

</style>
