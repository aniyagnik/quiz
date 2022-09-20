<template>
  <div class="home">
    <b-card title="Test Your skills!!!" sub-title="       Give a quiz on your favourite topic...        ">
    <QuizCategory
      :dropdownOptions="dropdownOptions"
      :handleCategory="handleCategory"
    />
    <b-button
      class="mt-3"
      variant="outline-primary"
      @click="submitUsersQuery"
      :disabled="!isCategory"
      >Start quiz</b-button
    >
    </b-card>
  </div>
</template>

<script>
import QuizCategory from "../components/quizCategory.vue";
export default {
  name: "home",
  components: {
    QuizCategory,
  },
  data() {
    return {
      dropdownOptions: [
        {
          text: "Select a Category for quiz",
          code: -1,
        },
        {
          text: "General Knowledge",
          code: 9
        },
        {
          text: "Entertainment: Books",
          code: 10
        },
        {
          text: "Entertainment: Films",
          code: 11
        },
        {
          text: "Entertainment: Music",
          code: 12
        },
        {
          text: "Entertainment: Television",
          code: 14
        },
        {
          text: "Entertainment: Video Games",
          code: 15
        },
        {
          text: "Entertainment: Board Games",
          code: 16
        },
        {
          text: "Entertainment: Japanese Anime &amp; Manga",
          code: 31
        },
        {
          text: "Entertainment: Cartoon &amp; Animations",
          code: 32
        },
        {
          text: "Science &amp; Nature",
          code: 17
        },
        {
          text: "Science: Computers",
          code: 18
        },
        {
          text: "Science: Mathematics",
          code: 19
        },
        {
          text: "Mythology",
          code: 20
        },
        {
          text: "Sports",
          code: 21
        },
        {
          text: "Geography",
          code: 22
        },
        {
          text: "History",
          code: 23
        },
        {
          text: "Politics",
          code: 24
        },
        {
          text: "Art",
          code: 25
        },
        {
          text: "Celebrities",
          code: 26
        },
        {
          text: "Animals",
          code: 27
        },
        {
          text: "Vehicles",
          code: 28
        },
      ],
      selectedCategory: -1,
      isCategory: false,
    };
  },
  methods: {
    handleCategory(code) {
      if (code == -1) this.isCategory = false;
      else this.isCategory = true;

      this.selectedCategory = code;
      console.log(this.selectedCategory, this.isCategory);
    },
    submitUsersQuery() {
      this.$router.push(`/quiz/${this.selectedCategory}`);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.bv-example-row {
  margin-top: 15px;
}
</style>
