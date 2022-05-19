<template>
<form action="" class="question-form">
        <input type="text" class="question__field" />
        <div class="question-type-wrapper">
          <input
            class="form__checkbox"
            type="checkbox"
            id="single-answer"
            name="single-answer"
            value="single"
          />
          <label for="single-answer">Single answer</label>
          <input
            class="form__checkbox"
            type="checkbox"
            id="multiple-answer"
            name="multiple-answer"
            value="multiple"
          />
          <label for="multiple-answer">Multiple answer</label>
        </div>
        <div class="answers">
          <div class="answer">
            <input type="text" class="answer__field" />
            <input type="checkbox" class="form__checkbox" />
          </div>
          <div class="answer">
            <input type="text" class="answer__field" />
            <input type="checkbox" class="form__checkbox" />
          </div>
          <div class="answer">
            <input type="text" class="answer__field" />
            <input type="checkbox" class="form__checkbox" />
          </div>
          <div class="answer">
            <input type="text" class="answer__field" />
            <input type="checkbox" class="form__checkbox" />
          </div>
          <button class="add-answer button">add answer</button>
        </div>
        <button class="push-question button">push question</button>
      </form>
</template>

<script>
export default {

}
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