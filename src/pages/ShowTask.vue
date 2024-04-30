<script>
import axios from 'axios';

export default {
    name: 'ShowTask',
    data() {
        return {
            task: [],
        }
    },
    methods: {
        getTask() {
            axios
                .get('http://127.0.0.1:8000/api/tasks/' + this.$route.params.id)
                .then(response => {
                    console.log(response.data);
                    this.task = response.data.task;
                })
        }
    },
    created() {
        this.getTask();
    } 
}
</script>

<template>
    <div class="container mt-3">

        <h2>{{ task.title }}</h2>

        <p>{{ task.description }}</p>

    </div>
</template>

<style lang="scss" scoped></style>