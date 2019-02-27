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
      <label for="bought">
        Bought
        <input v-model="bookData.ownership" type="radio" name="ownership" value="bought">
      </label>
      <label for="borrowed">
        Borrowed
        <input v-model="bookData.ownership" type="radio" name="ownership" value="borrowed">
      </label>
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
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
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
