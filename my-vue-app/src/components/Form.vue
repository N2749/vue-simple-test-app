<template>
  <form class="question-form" @submit.prevent>
    <input type="text" class="question__field" v-model="this.question.title" />
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
          name="answerMultiple"
          type="checkbox"
          class="form__checkbox"
          v-model="answer.isCorrect"
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
        answers: [
          { title: "", isCorrect: false },
          { title: "", isCorrect: false },
          { title: "", isCorrect: false },
          { title: "", isCorrect: false },
        ],
        correct: [],
      },
    };
  },
  methods: {
    addAnswer() {
      this.question.answers.push(
          { title: "", isCorrect: false });
    },
    check() {
      if (this.question.title === "") {
        alert("blank title");
        return false;
      }
      let singularity = false;
      for (const answer of this.question.answers) {
        if (answer.title === "") {
          alert("answer title is blank");
          return false;
        }
        if (answer.isCorrect) {
          singularity = answer.isCorrect;
        }
      }
      if (!singularity) {
        alert("no correct answer was selected");
        return false;
      }
      return true;
    },
    addCorrectAnswers() {
      if (this.question.correct.length !== 0) {
        this.question.correct.length = [];
      }
      for (const answer of this.question.answers) {
        if (answer.isCorrect) {
          this.question.correct.push(answer);
        }
      }
      alert(this.question.correct);
    },
    pushQuestion() {
      if (!this.check()) {
        return;
      }
      this.addCorrectAnswers();
      //TODO: push question to parent
      
      location.reload();
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
