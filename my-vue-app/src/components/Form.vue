<template>
  <form class="question-form" @submit.prevent>
    <input type="text" class="question__field" v-model="this.question.title" />
    <div class="question-type-wrapper">
      <input
        class="form__checkbox"
        type="radio"
        id="single-answer"
        name="type-answer"
        value="single"
        v-model="this.question.type"
        @change="blankCorrect"
      />
      <label for="single-answer">Single answer</label>
      <input
        class="form__checkbox"
        type="radio"
        id="multiple-answer"
        name="type-answer"
        value="multiple"
        v-model="this.question.type"
      />
      <label for="multiple-answer">Multiple answer</label>
    </div>
    <div class="answers">
      <div
        class="answer"
        v-for="answer in question.answers"
        :key="answer.title"
      >
        <input
          type="text"
          class="answer__field"
          :value="answer.title"
          @blur="(event) => (answer.title = event.target.value)"
        />
        <input
          v-if="this.question.type === 'multiple'"
          name="answer"
          type="checkbox"
          class="form__checkbox"
          v-model="answer.isCorrect"
        />
        <input
          v-else
          type="radio"
          class="form__checkbox"
          name="answer"
          v-model="answer.isCorrect"
          value="true"
          @blur="(event) => (answer.isCorrect = false)"
          @change="(event) => (answer.isCorrect = true)"
        />
      </div>
      <button class="add-answer button" @click="addAnswer">add answer</button>
    </div>
    <button class="push-question button" @click="pushQuestion">
      push question
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      question: {
        title: "",
        type: "",
        answers: [{ title: "c" }, {}, {}, {}],
        correct: [],
      },
    };
  },
  methods: {
    addAnswer() {
      this.question.answers.push({});
    },
    check() {
      //TODO: validate blankliness
      return false;
    },
    addCorrectAnswers() {
      //TODO: adding correct answers
    },   
    pushQuestion() {
      if (!this.check) {
        alert("something wrong!");
      }
      this.addCorrectAnswers();
      //TODO: push question to parent
      this.clearFields();
    },
    clearFields() {
      //TODO: refreshing inputs
    },
    blankCorrect() {
      this.question.answers.forEach((answer) => {
        answer.isCorrect = false;
      });
      this.question.correct = [];
    },
  },
};
</script>

<style>
.question-form {
  background-color: #fff;
  padding: 20px 0 20px 0;
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px 0;
  border-radius: 10px;
  font-size: 1.8rem;
}

.question__field {
  width: 80%;
  height: 50px;
  background-color: #e9eef1;
  border: none;
  border-radius: 10px;
  font-size: 1.8rem;
}

.question-type-wrapper {
  display: flex;
  align-items: center;
  gap: 0 5px;
}

.question__field:focus {
  outline: none;
}

.answers {
  width: 80%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px 0;
}

.answer {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.answer__field {
  width: 80%;
  padding: 0 5px;
  height: 50px;
  background-color: #e9eef1;
  border: none;
  border-radius: 10px;
  padding: 0 15px 0 15px;
  font-size: 1.8rem;
}

.form__checkbox {
  display: inline-block;
  width: 30px;
  height: 30px;
}

.button {
  border: none;
  border-radius: 10px;
  background-color: #f25c05;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 1.8rem;
  height: 50px;
}

.add-answer {
  width: 40%;
}

.push-question {
  width: 50%;
}
</style>
