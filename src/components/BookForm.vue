<template>
  <form v-on:submit.prevent="bookSubmit(bookData)" class action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value placeholder="Book Author">

    <div class="special">
      <label for="finishedReading">
        Finished Reading
        <input v-model="bookData.finishedReading" type="checkbox" name="finishedReading">
      </label>
    </div>

    <div>
      <form>
      <label for="ownership">
        Bought
        <input v-model="bookData.ownership" type="radio" name="ownership" value="Bought" >
      </label>
      <label for="ownership">
        Borrowed
        <input v-model="bookData.ownership" type="radio" name="ownership" value="Borrowed" >
      </label>
      </form>
    </div>
    <div class="special">
      <button type="submit" name="button">Add Book</button>
    </div>
  </form>
</template>


<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: "",
        ownership: ""
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
this.bookData.bookTitle = '';
this.bookData.bookAuthor = '';
this.bookData.finishedReading = false;
this.bookData.ownership= ''
event.target.reset();
    }


  }
};
</script>

<style>
.special {
  padding: 1em 0 0 0;
}

form {
  padding: 2em 0 0 0;
}

input {
  font-style: italic;
  border-color: green;
}
</style>
