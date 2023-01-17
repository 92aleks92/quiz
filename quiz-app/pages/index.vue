<template>
  <div class="w-screen h-screen bg-gray-100 flex items-center">
    <Question
      v-if="current_question <= questions.length - 1"
      @on-answer-selected="answerSelected"
      @on-next-question="current_question++"
      :question="questions[current_question]"
    />
    <Results v-else :questions="questions" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      current_question: 0, //index
      questions: [
        {
          title: "What is CSS?",
          correct_answer: 0,
          selected_answer: null,
          answers: [
            "This is a web styling lang",
            "A car part",
            "This is sweat cake",
          ],
        },
        {
          title: "What is HTML?",
          correct_answer: 1,
          selected_answer: null,
          answers: ["Town", "Hyper text markup lang"],
        },
        {
          title: "Is PHP compilable ?",
          correct_answer: 1,
          selected_answer: null,
          answers: ["True", "False"],
        },
      ],
    };
  },

  methods: {
    answerSelected(index) {
      if (this.questions[this.current_question].selected_answer != null)
        return false;
      this.questions[this.current_question].selected_answer = index;
    },
  },
};
</script>
