<template>
  <div>
    <QuizCategory
      :dropdownOptions="dropdownOptions"
      :selectCategory="selectCategory"
    />
    <b-button variant="outline-primary" @click="submitUsersQuery"
      >Start quiz</b-button
    >
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
          text: "geography",
          code: 22,
        },
        {
          text: "history",
          code: 21,
        },
      ],
    };
  },
  methods: {
    selectCategory(code) {
      this.selectedCategory = code;
      console.log(this.selectedCategory);
    },
    submitUsersQuery() {
      this.$router.push("/quiz");
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
