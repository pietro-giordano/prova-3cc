<script>
import axios from 'axios';

export default {
    name: 'CreateTask',
    data() {
        return {
            newTitle: "",
            newDescription: "",
        }
    },
    methods: {
        createTask() {
            axios
                .post('http://127.0.0.1:8000/api/tasks', {
                    title: this.newTitle, 
                    description: this.newDescription,
                })
                .then(response => {
                    console.log(response.data);
                })
                .catch(function (error) {
                    console.log(error);
                });
        }
    },
}
</script>

<template>
    <div class="container mt-3">

        <form>
            <div class="mb-3">
                <label for="title" class="form-label">Title</label>
                <input type="text" class="form-control" id="title" v-model="newTitle">
            </div>

            <div class="mb-3">
                <label for="description" class="form-label">Description</label>
                <textarea class="form-control" id="description" rows="3" v-model="newDescription"></textarea>
            </div>

            <button @click="createTask()" type="submit" class="btn btn-primary">Submit</button>
        </form>

        <router-link class="btn btn-primary mt-4" :to="{ name: 'homepage' }">
            Back
        </router-link>

    </div>
</template>

<style lang="scss" scoped></style>