<template>
  <input type="radio" id="one" value="Create" v-model="picked" />
  <label for="one">Create</label>
  <br />
  <input type="radio" id="two" value="Take" v-model="picked" />
  <label for="two">Take</label>
  <br />
  <create-page v-if="picked === 'Create'"></create-page>
  <take-page v-else></take-page>
</template>

<script>
import CreatePage from "../src/pages/CreatePage.vue";
import TakePage from "../src/pages/TakePage.vue";

export default {
  components: { CreatePage, TakePage },
  data() {
    return{
      picked: "Create"
    }
  }
};
</script>

<style></style>
