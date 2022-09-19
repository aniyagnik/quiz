<template>
  <div id="app">
    <LoadingBar :isLoading="isLoading" />
    <div v-if="!isLoading">
      <Header :correctAns="correctAns" :totalQue="index + 1" />
      <b-container class="bv-example-row">
        <b-row>
          <b-col sm="6" offset="3">
            <QuestionBox
              v-if="questions.length"
              :currentQuestion="questions[index]"
              :number="index + 1"
              :next="next"
              :incrementCorrect="incrementCorrect"
              :correctAns="correctAns"
              :isCompleted="isCompleted"
            />
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import QuestionBox from "./components/questionBox.vue";
import LoadingBar from "./components/LoadingBar";
import Header from "./components/header.vue";
export default {
  name: "app",
  components: {
    Header,
    QuestionBox,
    LoadingBar,
  },
  data() {
    return {
      questions: [],
      index: 0,
      correctAns: 0,
      isCompleted: false,
      isLoading: true,
    };
  },
  methods: {
    next() {
      if (this.index != 9) this.index++;
      else this.isCompleted = true;
    },
    incrementCorrect() {
      this.correctAns++;
    },
  },
  mounted: function() {
    fetch("https://opentdb.com/api.php?amount=10&category=22&type=multiple", {
      method: "get",
    })
      .then((response) => response.json())
      .then((data) => {
        this.isLoading = false;
        this.questions = data.results;
      });
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
