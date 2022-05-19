<template>
    <form @submit.prevent>
        <p>{{question.title}}</p>
        <div v-for="answer in question.answers" :key="answer">
            <input v-if="question.type" type="radio" name="">
            <input v-else type="checkbox" name="">
            <label for=""></label>
        </div>
        <input type="submit" value="check" @click="check()">
    </form>
</template>

<script>
export default {
    props: {
        question: {
            type: Object,
            required: true,
        },
    },

    methods: {
        check() {

        }
    }
}
</script>

<style>

</style>