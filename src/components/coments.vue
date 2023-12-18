<template>
    <div class="w-1/2 p-5 flex flex-col gap-y-5 overflow-y-scroll h-[900px]">

        <div v-for="Co, i in coments" :key="Co.id" class="w-full border-2 rounded border-black p-3 flex flex-col gap-y-3">
            <h2 class="text-3xl font-bold"> </h2>
            <h2> Asunto: {{ Co.title }}</h2>
            <h2> user id {{ Co.userId }}
            </h2>
            <div class="flex flex-col gap-y-0.5">
                <h2>texto:</h2>
                <h2>{{ Co.body }}</h2>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';


export default {

    data() {
        return {
            coments: null,
            clients: null

        }

    },
    mounted() {
        this.getcoments();
        this.getclients();
    },
    methods: {
        getcoments() {
            axios.get('https://jsonplaceholder.typicode.com/posts').then(
                response => {
                    this.coments = response.data
                }
            );
        },
        getclients() {
            axios.get('https://jsonplaceholder.typicode.com/users').then(
                response => {
                    this.clients = response.data
                }
            );
        }
    }

}
</script>
