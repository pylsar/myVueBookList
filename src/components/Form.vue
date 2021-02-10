<template>
    <form class="form" @submit.prevent="addBook">
        <div class="form__content">
            <div class="form__item">
                <label for="title">Название</label>
                <input type="text" id="title" v-model="titleValue" required>
            </div>
            <div class="form__item">
                <label for="author">Автор</label>
                <input type="text" id="author" v-model="authorValue" required>
            </div>
            <div class="form__item">
                <label for="rating">Рейтинг</label>
                <input type="number" id="rating" v-model="numberValue" required>
            </div>
        </div>
        <button class="btn__add" type="submit" :disabled="numberValue <=0">Add Book</button>
    </form>
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
<style lang="scss">
    form{
      display: flex;
      width: 100%;
      padding-bottom: 50px;
    }
    .btn__add{
      width: 20%;
      cursor: pointer;
    }
    .form__content{
      flex: 1;
    }
    .form__item{
      display: flex;
      width: 100%;
      height: 30px;
      & label{
          width: 30%;
      }
      & input{
        flex: 1;
        outline: none;
      }
    }
</style>


